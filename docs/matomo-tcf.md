# Matomo + TCF

Steuern von Matomo mithilfe einer TCF Consent Management Platform

## Integration

Um Matomo mithilfe einer TCF CMP zu steuern, müssen entsprechende
Signale an Matomo übergeben werden.

1. Matomo mitteilen, dass es ohne entsprechenden Consent nicht tracken
   / keine Cookies setzen darf
2. Matomo mitteilen, dass Consent gegeben wurde

Um Informationen über den aktuellen Consent eines Users zu erhalten
kommt die TCF API zum Einsatz.

## Code Beispiel

Im Beispiel unten kommt die API zum Einsatz um zu prüfen,
ob es Rechtsgrundlagen für Zweck 1, 2, 4, 8 und 10 gibt.
Falls ja wird Matomo aktiviert. Eine übersicht über alle TCF Zwecke finden Sie [hier](https://iabeurope.eu/iab-europe-transparency-consent-framework-policies/).

```js
// example matomo tracking code
//
var _paq = (window._paq = window._paq || []);

// let matomo know to wait for consent
_paq.push(["requireConsent"]);

// regular matomo tracking code
_paq.push(["trackPageView"]);
_paq.push(["enableLinkTracking"]);
(function () {
  var u = "//{$MATOMO_URL}/";
  _paq.push(["setTrackerUrl", u + "matomo.php"]);
  _paq.push(["setSiteId", { $IDSITE }]);
  var d = document,
    g = d.createElement("script"),
    s = d.getElementsByTagName("script")[0];
  g.type = "text/javascript";
  g.async = true;
  g.src = u + "matomo.js";
  s.parentNode.insertBefore(g, s);

  // event listener to enable matomo tracking on consent given
  window.__tcfapi("addEventListener", 2, function (tcData, listenerSuccess) {
    if (listenerSuccess) {
      if (
        tcData.eventStatus === "useractioncomplete" ||
        tcData.eventStatus === "tcloaded"
      ) {
        if (
          tcData.purpose.consents[1] &&
          tcData.purpose.consents[2] &&
          (tcData.purpose.consents[4] || tcData.purpose.legitimateInterests[4])(
            tcData.purpose.consents[8] || tcData.purpose.legitimateInterests[8],
          )(
            tcData.purpose.consents[10] ||
              tcData.purpose.legitimateInterests[10],
          )
        ) {
          _paq.push(["setConsentGiven"]);
        }
      }
    }
  });
})();
```
