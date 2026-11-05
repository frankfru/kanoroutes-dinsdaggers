# Kajakroutes Dinsdaggers

Een interactieve Leaflet-kaart met kajakroutes uit Noord-Holland en omgeving. De slogan in de kop linkt naar de routebeschrijvingen van AKV Odysseus. Donkere, verzadigde routekleuren met een lichte omlijning houden de routes goed zichtbaar op de kaart.

## Lokaal bekijken

Installeer Node.js en start de lokale webserver vanuit deze map:

```powershell
node server.js
```

Open daarna [http://localhost:4173](http://localhost:4173).

De knoppen **Kajakroutes** en **Kajakroute-heatmap** schakelen de kaartlagen onafhankelijk van elkaar aan en uit, zodat beide tegelijk zichtbaar kunnen zijn. De heatmap combineert de kajakroutes op de kaart met lokale GPX-opnames. Elk routevak van ongeveer 25 meter telt maximaal één keer per route of opname mee, zodat vaker bevaren stukken sterker oplichten. De vlekstraal en vervaging worden aangepast aan het zoomniveau om de heatmap bij uitzoomen compacter te houden.

De heatmap wordt vooraf lokaal gegenereerd; GitHub Pages heeft geen server nodig. De site downloadt alleen `kayak-heatmap-data.json`, niet de ruwe GPX-bestanden. De geaggregeerde heatmapdata is wel openbaar en kan routes tot ongeveer 25 meter nauwkeurig tonen. Neem het JSON-bestand op in de Pages-publicatie, maar publiceer de bron-GPX-bestanden niet. Als de heatmap aanstaat, kun je de intensiteit, vlekbreedte en het kleurcontrast live aanpassen. De standaardwaarden zijn `1.0×`, `1.0×` en `1.0×`; pas ze aan in `HEATMAP_DEFAULTS` in `index.html`.

De luchtfoto van PDOK en Natura 2000-gebieden zijn beschikbaar via de laagkeuze; Natura 2000 is een transparante overlay die tegelijk met een achtergrondkaart kan worden getoond. De TOP25raster-laag is alleen beschikbaar tussen schaal 1:50.000 en 1:4.000; bij het kiezen van die laag wordt de kaart automatisch naar dat zoombereik aangepast. De Kadastrale kaart van PDOK gebruikt de standaardvisualisatie en wordt getoond vanaf zoomniveau 17. De kadastrale grenzen geven alleen een indicatie van de ligging; er kunnen geen maten aan worden ontleend.

## Routedata vernieuwen

- Haal de Noord-Holland-routes en bijbehorende PDF-links opnieuw op met `node build-noord-holland-routes.js`.
- Genereer de heatmap opnieuw na het toevoegen of wijzigen van GPX-opnames met `node build-kayak-heatmap.js`. Het script leest standaard uit `D:\Dinsdaggers\whatsapp` en schrijft `kayak-heatmap-data.json` in deze map. Stel voor een andere bronmap de omgevingsvariabele `KAYAK_GPX_DIRECTORY` in.

De route-lijst toont de afstand in hele kilometers achter de routenaam. De route-pop-up toont de berekende afstand in kilometers en links naar de oorspronkelijke GPS-bestanden en routepagina's. Een groene stip markeert het startpunt van de geselecteerde route. De routes worden vereenvoudigd voor een vlotte weergave; de afstand is daarop gebaseerd.

Op mobiel kun je het routepaneel vanaf de handgreep omhoog slepen en na het kiezen van een route weer omlaag schuiven. Met de knop rechtsboven open je de kaart schermvullend. De routes hebben een bredere, onzichtbare klikzone zodat selecteren op touchscreens makkelijker is.

## Een route delen

Selecteer een route in de lijst om de deelbare URL bij te werken. De link zoomt in op de route en toont de routebeschrijving. Bijvoorbeeld:

`?route=1-1-grachten-van-alkmaar`

## Bronnen

- Noord-Holland-routes en clublogo: [AKV Odysseus](https://www.akvodysseus.nl/). Het routeoverzicht is samengesteld door Peter Groen; de routes staan op de pagina [Routes kanotochten](https://www.akvodysseus.nl/disciplines/toerkano/routes-kanotochten/).
- Achtergrondkaarten en overlays: [OpenStreetMap](https://www.openstreetmap.org/copyright), [OpenTopoMap](https://opentopomap.org/), de BRT-Achtergrondkaart, [luchtfoto](https://www.pdok.nl/) en TOP25raster via [PDOK](https://www.pdok.nl/), de [Kadastrale kaart](https://www.pdok.nl/introductie/-/article/kadastrale-kaart) en Natura 2000 via RVO/PDOK.
