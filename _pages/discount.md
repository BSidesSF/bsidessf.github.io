---
layout: default
---

<script>
  function $(elem) {
    return document.getElementById(elem);
  }

  function processCode() {
    $('status').innerHTML = "Please wait...";
    $('loading').style = 'visibility:visible';

    function callback() {
      r = JSON.parse(this.responseText);
      $('loading').style = 'visibility:hidden';

      if (r['status'] == 'ok')
        $('status').innerHTML = '<span style="font-weight:bold;color:green">Done!</span> Please check your inbox (and spam!) for your discount code.';

      if (r['status'] == 'fail') {
        if (r['reason'] == 'notedu')
          $('status').innerHTML = '<span style="font-weight:bold;color:red">Error:</span> Please use an address provided by an academic institution or reach out to tickets@bsidessf.org for assistance.';
        if (r['reason'] == 'exists')
          $('status').innerHTML = '<span style="font-weight:bold;color:red">Error:</span> Code already claimed by this address.';
      }
    }

    email = JSON.stringify({"email": $('email').value});
    req = new XMLHttpRequest();
    req.addEventListener('load', callback);
    req.open('POST', 'https://990onl09j9.execute-api.us-east-1.amazonaws.com/prod/studentDiscount');
    req.setRequestHeader("Content-Type", "application/json");
    req.send(email);
  }
</script>

<article class="row">
  <section class="post-content">

    <h2><b>BSidesSF 2022</b></h2>

    <p>
       If you're a student or otherwise in academia, please use the form below with the email address provided by your institution.
       Please reach out to <b>tickets@bsidessf.org</b> if you need assistance or would like to request a discount for other reasons.<br/>
    </p>

    <form onsubmit="processCode(); return false">
      <div style="text-align:center">
      <p>
        <input style="height: 40px; width: 500px;" id="email" type="email" length="64" placeholder="Email Address"/>
      </p>
      <p>
        <input type="submit" value="Request discount"/>
      </p>
      <p>
        <span id="status"></span>  <img id="loading" style="visibility:hidden" src="data:image/gif;base64,R0lGODlhEAAQAPIAAP///wAAAMLCwkJCQgAAAGJiYoKCgpKSkiH/C05FVFNDQVBFMi4wAwEAAAAh/hpDcmVhdGVkIHdpdGggYWpheGxvYWQuaW5mbwAh+QQJCgAAACwAAAAAEAAQAAADMwi63P4wyklrE2MIOggZnAdOmGYJRbExwroUmcG2LmDEwnHQLVsYOd2mBzkYDAdKa+dIAAAh+QQJCgAAACwAAAAAEAAQAAADNAi63P5OjCEgG4QMu7DmikRxQlFUYDEZIGBMRVsaqHwctXXf7WEYB4Ag1xjihkMZsiUkKhIAIfkECQoAAAAsAAAAABAAEAAAAzYIujIjK8pByJDMlFYvBoVjHA70GU7xSUJhmKtwHPAKzLO9HMaoKwJZ7Rf8AYPDDzKpZBqfvwQAIfkECQoAAAAsAAAAABAAEAAAAzMIumIlK8oyhpHsnFZfhYumCYUhDAQxRIdhHBGqRoKw0R8DYlJd8z0fMDgsGo/IpHI5TAAAIfkECQoAAAAsAAAAABAAEAAAAzIIunInK0rnZBTwGPNMgQwmdsNgXGJUlIWEuR5oWUIpz8pAEAMe6TwfwyYsGo/IpFKSAAAh+QQJCgAAACwAAAAAEAAQAAADMwi6IMKQORfjdOe82p4wGccc4CEuQradylesojEMBgsUc2G7sDX3lQGBMLAJibufbSlKAAAh+QQJCgAAACwAAAAAEAAQAAADMgi63P7wCRHZnFVdmgHu2nFwlWCI3WGc3TSWhUFGxTAUkGCbtgENBMJAEJsxgMLWzpEAACH5BAkKAAAALAAAAAAQABAAAAMyCLrc/jDKSatlQtScKdceCAjDII7HcQ4EMTCpyrCuUBjCYRgHVtqlAiB1YhiCnlsRkAAAOwAAAAAAAAAAAA=="/>
      </p>
      </div>
    </form>

    <p>
       Free tickets are also available for volunteers with a six hour time commitment. Check out our <a href="/volunteer.html">volunteer opportunities</a> and help us make BSidesSF 2022 a success!
    </p>
  </section>

</article>
