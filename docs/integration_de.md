CommonMedia AdScript Integration
======

CommonMedia Ad-Script (cmAds) Integrations Leitfaden
----------------------------------------------------

Das CommonMedia Ad-Script (cmAds) ist das Rückgrat des CommonMedia Ad-Stacks. Es ist verantwortlich für all die Dinge, die für eine erfolgreiche Monetarisierung ihrer Website nötig sind. Unter anderem für: Real-Time-Bidding, Id- und Key-Value-Management, Lazy-Loading und die Kommunikation mit dem Ad-Server. Die Integration ist sehr einfach und benötigt nur wenige Schritte.

## Script Tag

Der Script-Tag, den Sie von ihrem Account Manager erhalten haben, muss innerhalb des `<head>` Elements Ihrer Website eingefügt werden. Er sollte auf jeder Unterseite vorhanden sein, selbst wenn dort keine Werbung angezeigt werden soll.

Beispiel

```html
<html lang="de">
<head>
  <meta charset="UTF-8">
  <title>Beispiel</title>
  <script async type='text/javascript' src='https://www.cmadserver.de/ads/?site=beispiel'></script>
</head>
<body>
  ...
</body>
</html>
```

## Parameter

Sie können das Verhalten des Ad-Scripts verändern, indem sie weitere Query-Parameter an die URL anhängen.

### Keine Werbung

If you pass `noads=true` as query parameter, no ads will be rendered on the page. This is especially useful for sub-pages where no ads should be visible, but all other services of cmAds should still be running.

Wenn sie `noads=true` als Query-Parameter hinzufügen, werden keine Werbungen auf der jeweiligen Seite abgerufen und angezeigt. Das ist besonders nützlich, sollte ihre Website Unterseiten haben, auf denen keine Werbungen zu sehen sein sollen, weitere Dienste des cmAds-Stacks aber dennoch aktiv sein sollten.

```html
  <script async type='text/javascript' src='https://www.cmadserver.de/ads/?site=example&noads=true'></script>
```

## Ad-Container

CmAds kann Werbe-Container auf ihrer Website einfügen, wenn Sie dies wünschen. Allerdings ist davon abzuraten, denn es erhöht den Layout Shift (CLS) ihrer Website. Stattdessen sollten die Werbe-Container direkt im Source-Code Ihrer Website eingefügt werden. CmAds bietet zwei verschiedene Möglichkeiten diese Container zu definieren:

### Class-Container

Class-Container werden nur dann aktiv, wenn sie in die Nähe des Viewports des Nutzers kommen (Lazy Loading). Das kann sowohl die Performance Ihrer Website verbessern, als auch die KPIs der Werbeplatzierung. Class-Container sind besonders dann nützlich, wenn Platzierungen dynamisch innerhalb des Contents vorgenommen werden (z.B. nach jedem vierten Absatz). Um einen Class-Container auf Ihrer Website zu platzieren, fügen sie einen der folgenden Container dort ein wo Werbung gezeigt werden soll:

**Mobile Layouts**

```html
<div class="cm-ad-content" style="min-height:505px;"><div>
```

**Desktop Layouts**

```html
<div class="cm-ad-content" style="min-height:275px;"><div>
```

`min-height` wird zu dem Container hinzugefügt um CLS zu vermeiden wenn die Werbung lädt. Die Styles können inline oder über ein Stylesheet gesetzt werden.

### Id-Container

Id-Container are statically placed containers, which are rendered immediately on page load. They are especially useful for out-of-page ads and ads that are outside of the content area. To place an id-container on your page, add the following element to your website's source code:

Id-Container sind statisch platzierte Container, welche sofort beim Seitenaufruf geladen werden. Sie sind besonders nützlich um out-of-page Werbung und Werbung außerhalb des Contents zu platzieren. Um einen Id-Container auf Ihrer Website zu platzieren, fügen sie einen der folgenden Container dort ein wo Werbung gezeigt werden soll:

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

`min-height` wird zu dem Container hinzugefügt um CLS zu vermeiden wenn die Werbung lädt. Die Styles können inline oder über ein Stylesheet gesetzt werden.
