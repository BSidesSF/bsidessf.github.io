BSidesSF Website
=================

Theme is based on [Slim Pickins](https://chrisanthropic.github.io/slim-pickins-jekyll-theme/).

Thanks to [ShmooCon](http://shmoocon.org/) for some navigation and content help.

#Who can contribute to this project



Running Locally
=================

If you haven't run this previoiusly, start with ```bundle install``` to install all of the gems necessary for the site.

To run the site locally, run ```bundle exec jekyll serve``` or ```rake watch``` on the command line. The address will be listed as ```Server address``` in the output when this runs correctly.

Adding pages
============

You can create a new page in \_pages, which will generate the page at the root of the site.  The top of your page (md or html) should look like:

```
---
layout: page
title: "My Page Title"
---
```

After that you can put your content in either html or md form, depending on your file extension.   _filename_.md will become `filename.html`

If you want the page to be linked, you should update __\_data/nav.yml__ with the proper
location in the navigation.
