CommonMedia AdScript Integration
======

Anleitung zur Einbindung des CommonMedia AdScripts (cmAds)
----------------------------------------------------

Das CommonMedia AdScript (cmAds) ist Rückgrat des CommonMedia Ad-Stacks. Es übernimmt sämtliche Aufgaben die für eine erfolgreiche Monetarisierung einer Website notwendig sind, unter anderem: Real-Time-Bidding, Id- und Key-Value-Management, Lazy Loading und die Kommunikation mit dem AdServer. Für die Einbindung sind nur wenige Schritte notwendig.

## Script Tag

Der cmAds-Tag den Sie von ihrem Account Manager erhalten haben, muss im <head> Element ihrer Website eingebunden werden. Er sollte auf jeder einzelnen Unterseite ihrer Website vorhanden sein, selbst wenn dort keine Werbung angezeigt wird.

Beispiel

```html
<html lang="de">
<head>
  <meta charset="UTF-8">
  <title>Beispiel Seite</title>
  <script async type='text/javascript' src='https://www.cmadserver.de/ads/?site=beispiel'></script>
</head>
<body>
  ...
</body>
</html>
```

## Ad-Container

CmAds ist dazu in der Lage Werbe-Container für Sie zu platzieren, allerdings raten wir dazu ab um Cumulative Layout Shift (CLS) zu vermeiden. Stattdessen sollten Sie im Source Code ihrer Website selbst definieren an welcher Stelle Werbung platziert werden soll. Wir bieten dazu zwei Unterschiedliche Möglichkeiten

### Class-Container

Class-Container werden erst dann geladen, wenn sie in die nähe des Viewports des Users kommen (Lazy Loading), was sich positiv auf die KPIs der Platzierung auswirken kann. Class-Container eignen sich vor allem für dynamische Platzierungen im Content (bpsw. nach jedem 4. Absatz). Um einen Class Container zu platzieren fügen Sie im Source Code ihrer Website einfach folgendes Element ein:

```html
<div class="cm-ad-content"><div>
```

### Id-Container

Id-Container sind fest platzierte Container die direkt beim Aufruf der Seite geladen werden. Sie eigenen sich vor allem für Out-Of-Page Ads. Um einen Id-Container zu platzierten fügen Sie im Source Code ihrer Website einfach eins der folgenden Elemente ein:

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
<div id="BB"><div>
```

## Parameter

Das Verhalten des cmAds-Tags lässt sich durch das anfügen von Parametern beliebig verändern.