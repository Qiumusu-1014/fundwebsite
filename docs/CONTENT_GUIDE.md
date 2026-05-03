# Content Update Guide

This site is static. Most recurring content now lives in the `data/` folder so new updates do not require editing page layout code.

## Add Homepage / News Page Items

Edit `data/news-data.js` and add a new object at the top of `window.siteNews`.

Required fields:

- `title`: article headline
- `date`: sorting date in `YYYY-MM-DD`
- `displayDate`: public date label
- `category`: one of `Infrastructure`, `Royal Activities`, `Technology`, `Economy`
- `image`: local path such as `images/new-photo.jpg` or a full image URL
- `excerpt`: short summary
- `link`: detail page path, usually `news_pages/news_new_11.html`

The homepage automatically shows the latest 3 items by `date`. The news page automatically handles filtering, search, and pagination.

## Add Photos To The Scrolling Gallery

1. Put the image in `images/`.
2. Add one object to `window.siteGallery` in `data/gallery-data.js`.

Example:

```js
{ image: "images/royal10.jpg", alt: "Royal engagement event" }
```

The homepage duplicates the list in JavaScript so the scrolling wall stays seamless.

## Update Leadership Names

Edit `window.siteLeaders` in `data/gallery-data.js`.

## Add Or Edit Recruitment Positions

Edit `window.siteJobs` in `data/jobs-data.js`.

Each job supports:

- `title`
- `location`
- `department`
- `experience`
- `icon`: Font Awesome icon class without `fa-solid`
- `summary`
- `responsibilities`: array of bullet strings
- `requirements`: array of bullet strings

The careers page automatically renders the cards and application modal.

## Application Receiving

Application submissions use `window.applicationSettings.formEndpoint` in `data/jobs-data.js`.

Current endpoint:

```text
https://formsubmit.co/ajax/recruit@uaeroyal.fund
```

FormSubmit may require first-time email activation for `recruit@uaeroyal.fund`. The modal also keeps a mailto fallback link so applicants can still send by email if the form endpoint has not been activated.