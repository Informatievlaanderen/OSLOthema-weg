# Datavoorbeelden

## Aanpassingen model

### Wegsegment
- `inLinkset` attribuut toegevoegd om te koppelen met EuropeseWeg en Weg
- `kruist` attribuut toegevoegd om kruisingen mee te koppelen, inverse van `kruisingVan`
- `detail` attribuut nodig om API response te linken bij die referentie naar wegsegmenten, niet toegevoegd.
- `type` attribuut nodig om aan te geven of het segment boven of onder kruist met een ander segment bij een ongelijksgrondsekruising. Niet toegevoegd.

### Straatnaam
- identificator
- detail veld voor API response link

### Geometrie
- wkt/gml bij Geometrie kunnen 0...* zijn (afhankelijk van coordinaatsysteem)

### Identificator
- gestructueerdeIdentificator attribuut

### GestructeerdeIdentificator
- Toegevoegd

### Wegknoop
- `segment` attribuut om segmenten te linken vanuit de Wegknoop die de knoop aan elkaar hangt.

### Transporteigenschap

Subklasse 'Grensknoop' toegevoegd maar lijkt me niet correct eerder codelijst?

## Aanpassingen API responses

### Wegsegment

`https://api.basisregisters.staging-vlaanderen.be/v3/wegsegmenten/51613`

- Identificator voorzien van `@type`.
- GestructeerdeIdentificator object correct gebruikt.
- `@id` met URI wegsegment naar de root gebracht omdat dit in Linked Data de URI is van het hele object.
- `wegsegmentGeometrie` -> `geometriemiddelijn` label aangepast
- `geometrieMethode` -> samengevoegd bij geometrie.
- Alle lineaire referentie eigenschappen samengevoegd in een array `referentie` wat uit te breiden is tot het oneindige indien er eigenschappen bijkomen zonder API velden te moeten bij te maken of te breken.

`https://api.basisregisters.staging-vlaanderen.be/v3/wegsegmenten/58726`

## Vragen

- Waarom niet `geometrie` voor zowel Wegsegment als Wegknoop ipv 2 verschillende attributen?