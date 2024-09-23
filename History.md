
# Add to the history of BSidesSF

Our basic method is to generate the static site from a previous year,
with some modifications to have it serve properly from it's new location.
Then we add it to the historical pages, and all should be good.

### git hashes for each year


| Year | Dates       | Commit to use                            |
| :--: | :---------- | :--------------------------------------- |
| 2010 | Mar 2 & 3   | N/A - pre gitlab pages work              |
| 2011 | Feb 14 & 15 | N/A - pre gitlab pages work              |
| 2012 | Feb 27 & 28 | N/A - pre gitlab pages work              |
| 2013 | Feb 24 & 25 | N/A - pre gitlab pages work              |
| 2014 | Feb 2 & 3   | N/A - pre gitlab pages work              |
| 2015 | Apr 19 & 20 | N/A - pre gitlab pages work              |                                         
| 2016 | Feb 28 & 29 | bc70ea06488b64721ceb6848310b3be49ce504b4 |
| 2017 | Feb 12 & 12 | ff918e9033beb883836b71152031c7a4afaa62fc |
| 2018 | Apr 15 & 16 | 26a2668a12d03135aff9fde3c126e39bdc246d93 |
| 2019 | Mar 3 & 4   | f4c0ad8b29ef50658ffcf9327043848aef0a73f2 |
| 2020 | Feb 23 & 24 | 97fc8093021afb200a579b77fd4ac95a89efb2f4 |
| 2021 | Mar 6 & 9   | b10ee2dd56362a20a3f8343699474d908803db9c | 
| 2022 | Jun 4 & 5   | 154ecfeb0c50cdc7e80b47f36bb2742d4f901fbd |
| 2023 | Apr 23 & 23 | 74123ef96c234ca2cce67c1640a924ad7d6975e7 |
| 2024 | May 4 & 5   | d36e0e7ab55c8009246121eeb47c4ead4c633b15 |
| 2025 | Apr 25 & 25 |


##### Process (this is detailed an finicky so be careful to check your work)

- Look for the last change during or right after the event to capture all of the changes that were made for the event.
  - `git log --decorate --until YYYY-MM-DD --graph --raw main`
- Use the hash from the previoous command to check out the right version of the site
  - `git checkout <hash>`
- this builds the full site with a specific baseurl to support the changed directory root. This allows us to iframe it and have the site render as it was, and not use the current styles.
  - `bundle exec jekyll build --baseurl /a/YYYY -d _archives/YYYY`
  - `git checkout <branch>` # this is the branch you are using to create the archive
- Create the archive index page
  - Create a file in `/\_archive` for the year you are archiving `_archive/YYYY.md` using the template below

```
---
layout: archive
year: YYYY
---
```

- Add an entry to /\_data/history.yml
- Verify that the archived site looks correct, especially at /a/YYYY.html

  - `bundle exec jekyll serve`
  - verify the About->Past Events page has your year and links on it
  - verify the website link works and is properly framed
  - verify all of the images and other assets are being properly loaded
    - the sponsors page can be a sign of problems, make sure it shows all sponsors for that event
    - you can also search in `_archive/YYYY` for `src="/` or `href="/` which aren't point to /a/YYYY

- Look for items from the year you are archiving that can be removed, and delete them
- Make the necessary commits to your branch
- PR your changes to this repository
