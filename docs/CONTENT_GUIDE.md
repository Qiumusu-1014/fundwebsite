# Content Update Guide

This site is static. Most recurring content now lives in the `data/` folder so new updates do not require editing page layout code.

## Add Homepage / News Page Items

Edit `data/news-data.js` and add a new object at the top of `window.siteNews`.

Required fields:

- `title`: article headline
- `date`: sorting date in `YYYY-MM-DD`
- `displayDate`: public date label
- `category`: one of `Infrastructure`, `Royal Activities`, `Technology`, `Economy`, `Energy Policy`, `Trade`, `Entrepreneurship`, `Macro Economy`, `Aviation`
- `image`: local path such as `images/new-photo.jpg` or a full image URL
- `excerpt`: short summary
- `link`: detail page path, usually `news_pages/news_new_11.html`
- `keywords`: search keywords shown as chips on the news page
- `featuredOnHome`: set to `true` for homepage news
- `homeOrder`: homepage order when `featuredOnHome` is used

The homepage shows up to 3 items marked with `featuredOnHome: true`, sorted by `homeOrder`. If no featured items are set, it falls back to the latest 3 items by `date`. The news page searches title, excerpt, category, source, display date, and `keywords`.

## Add Photos To The Scrolling Gallery

1. Put the image in `images/`.
2. Add one object to `window.siteGallery` in `data/gallery-data.js`.

Example:

```js
{ image: "images/royal10.jpg", alt: "Royal engagement event" }
```

The homepage duplicates the list in JavaScript so the scrolling wall stays seamless.

## Update Page Hero Images

The About, Careers, Contact, and News pages use local hero images in `images/`.

- `images/about-hero-ai.svg`: UAE architecture, skyline, and institutional vision
- `images/careers-hero-ai.svg`: empty executive workspace for recruitment
- `images/contact-hero-ai.svg`: UAE headquarters / location style
- `images/news-hero-ai.svg`: UAE economy, aviation, trade, and energy landscape

Keep these page hero images free of people, faces, readable text, logos, and watermarks so headings remain clear and the site keeps a formal institutional style.

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

## Google Pay Donations

The donation page includes a Google Pay-ready frontend in `donate.html`.

Current mode:

```js
environment: 'TEST'
gateway: 'example'
gatewayMerchantId: 'exampleGatewayMerchantId'
```

To accept live online donations, replace the test values in `GOOGLE_PAY_CONFIG` with the payment processor gateway values and merchant ID issued for UAE Royal Capital Funding. A server-side payment processor endpoint is also required before live launch because the browser should not directly complete settlement.
