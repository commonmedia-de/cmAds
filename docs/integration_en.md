CommonMedia AdScript Integration
======

CommonMedia Ad-Script (cmAds) Integration Guide
----------------------------------------------------

The CommonMedia ad-script (cmAds) is the backbone of the CommonMedia ad-stack. It is responsible for all task that are necessary for a successful monetization of digital properties. Some of which are: Real-Time-Bidding, id- and key-value-management, lazy loading and ad-server-communication. The integration is straight forward and will only take a couple of steps.

## Script Tag

The script-tag, that you received from your account manager, needs to be added inside the `<head>` element of your website. It should be present on every single page, no matter if ads should be shown there or not.

Example

```html
<html lang="de">
<head>
  <meta charset="UTF-8">
  <title>Example</title>
  <script async type='text/javascript' src='https://www.cmadserver.de/ads/?site=example'></script>
</head>
<body>
  ...
</body>
</html>
```

## Parameter

You can change the behaviour of cmAds by passing additional query-parameters to the script-tag.

### No Ads

If you pass `noads=true` as query parameter, no ads will be rendered on the page. This is especially useful for sub-pages where no ads should be visible, but all other services of cmAds should still be running.

```html
  <script async type='text/javascript' src='https://www.cmadserver.de/ads/?site=example?noads=true'></script>
```

## Ad-Container

CmAds can automatically inject ad containers for you if you wish so, although this is discouraged because it introduces layout shifts (CLS). Instead you should place ad containers directly in your websites source code, wherever ads should be rendered. CmAds offers two different kinds of containers for this:

### Class-Container

Class-containers are only rendered, when they come near a users viewport (Lazy Loading). This can increase website performance and the ads KPIs. Class-Container are especially useful for dynamic placements inside the content area (e.g., after every fourth paragraph). To place a class-container on your page, add the following element to your website's source code:

**Mobile Layouts**

```html
<div class="cm-ad-content" style="min-height:505px;"><div>
```

**Desktop Layouts**

```html
<div class="cm-ad-content" style="min-height:275px;"><div>
```

`min-height` is added to the containers styling in order to avoid CLS once ads render. You can set this inline or inside your stylesheet.

### Id-Container

Id-Container are statically placed containers, which are rendered immediately on page load. They are especially useful for out-of-page ads and ads that are outside of the content area. To place an id-container on your page, add the following element to your website's source code:

#### Sticky Sitebar

```html
<div id="SS"><div>
```

#### Floor Ad

```html
<div id="LB"><div>
```

#### Billboard

```html
<div id="BB" style="min-height:275px;"><div>
```

`min-height:275px` is added to the containers styling in order to avoid CLS once ads render. You can set this inline or inside your stylesheet.
