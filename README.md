# BSidesSF Website

Theme is based on [Slim Pickins](https://chrisanthropic.github.io/slim-pickins-jekyll-theme/).

Thanks to [ShmooCon](http://shmoocon.org/) for some navigation and content help.

# Running Locally

If you haven't run this previously, start with `bundle install` to install all of the gems necessary for the site.

To run the site locally, run `bundle exec jekyll serve` or `rake watch` on the command line. The address will be listed as `Server address` in the output when this runs correctly.

# Adding pages

You can create a new page in \_pages, which will generate the page at the root of the site. The top of your page (md or html) should look like:

```
---
layout: page
title: "My Page Title"
---
```

After that you can put your content in either html or md form, depending on your file extension. _filename_.md will become `filename.html`

If you want the page to be linked, you should update **\_data/nav.yml** with the proper
location in the navigation.

# Add to the history of BSidesSF

Our basic method is to generate the static site from a previous year,
with some modifications to have it serve properly from it's new location.
Then we add it to the historical pages, and all should be good.

| Year | Dates       | Commit to use                            |
| :--: | :---------- | :--------------------------------------- |
| 2016 | Feb 28 & 29 | bc70ea06488b64721ceb6848310b3be49ce504b4 |
| 2017 | Feb 12 & 12 | ff918e9033beb883836b71152031c7a4afaa62fc |
| 2018 | Apr 15 & 16 | 26a2668a12d03135aff9fde3c126e39bdc246d93 |
| 2019 | Mar 3 & 4   |
| 2020 | Feb 23 & 24 |
| 2021 | Mar 6 & 9   |
| 2022 | Jun 4 & 5   |
| 2023 | Apr 23 & 23 |

##### Process (this is detailed an finicky so be careful to check your work)

- Look for the last change during or right after the event to capture all of the changes that were made for the event.
  - `git log --decorate --until YYYY-MM-DD --graph --raw main`
- Use the hash from the previoous command to check out the right version of the site
  - `git checkout <hash>`
- **DO NOT SKIP** Make sure you have a completely CLEAN \_site directory. This is important.
  - `bundle exec jekyll clean`
- this builds the full site with a specific baseurl to support the changed directory root. This allows us to iframe it and have the site render as it was, and not use the current styles.
  - `bundle exec jekyll build --baseurl "/a/YYYY/"`
  - `mv _site _archive/YYYY`
  - `git checkout <branch>` # this is the branch you are using to create the archive
- Create the archive index page
  - Be sure to replace YYYY with the appropriate year
  - Create a file in \_archive for the year you are archiving `_archive/YYYY.html` using the template below

```html
<div class="archive banner">
  <strong class="banner">
    You're viewing an archive of the 2016 website.
  </strong>
</div>
<div class="archive">
  <iframe src="/a/YYYY" width="100%" height="1024">
    Loading YYYY site...
  </iframe>
</div>
```

- Add an entry to \_data/history.yml
- Verify that the archived site looks correct, especially at /a/YYYY.html

  - `bundle exec jekyll serve`
  - verify the About->Past Events page has your year and links on it
  - verify the website link works and is properly framed
  - verify all of the images and other assets are being properly loaded
    - you can also search in `_archive/YYYY` for `src="/` or `href="/` which aren't point to /a/YYYY

- You may need to edit any hardcoded referential paths that exist in `_archive/YYYY` to fix those links work properly inside the iframe

- Look for items from the year you are archiving that can be removed, and delete them

- Make the necessary commits to your branch
- PR your changes to this repository
