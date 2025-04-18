# syntra_eindwerk_birds

## Inleiding
Deze studie kadert in de eindproef voor de Syntra cursus "Python data developer".
Dit combineert mijn passie voor data, met mijn interesse in het vogelrijk.

Ik besloot te onderzoeken wat ik me al een tijd afvroeg. Heeft onze inheemse vogel, de boomklever, nadeel van de opmars van de exoot, de halsbandparkiet?

### Opmars van de halsbandparkiet
De halsbandparkiet werd in Vlaanderen voor het eerst waargenomen in 1962 in Tervuren. Het eerste broedgeval dateert van 1966, toen een paar zes jongen grootbracht in een vervallen paviljoen in het Park van Tervuren. De eigenlijke opmars begon pas in 1974 toen in het Meli Park in Brussel een 40-tal exemplaren werden losgelaten als speciale attractie voor de bezoekers. Deze populatie bleek levensvatbaar en verspreidde zich verder.

### Impact op de boomklevers
Halsbandparkieten zijn holenbroeders en geven de voorkeur aan oude nesten van de grote bonte specht. 

Net als halsbandparkieten hebben ook onze inheemse boomklevers een voorkeur voor oude nestgaten van de grote bonte specht. 
Halsbandparkieten starten eind november al met het verkennen van potentiële nestholten. Als de boomklevers in maart op zoek gaan naar een geschikte broedplaats, zijn de beste plaatsen vaak al bezet door halsbandparkieten, waardoor ze moeten uitwijken naar minderwaardige holtes. 
In gebieden waar veel halsbandparkieten zitten, zou het voor boomklevers moeilijk kunnen worden om een geschikte nestholte te vinden.

Op wikipedia vinden we terug dat, waar de halsbandparkiet terrein wint, de inheemse boomklever afneemt. In het ergste geval, zou een derde van de boomkleverpopulatie kunnen verdwijnen.

Maar kan dit ook aangetoond worden via de waarnemingen van boomklevers en halsbandparkieten op waarnemingen.be?
Is de evolutie van populatie van de boomklever hetzelfde in regio's waar de halsbandparkiet in opmars is, als waar de halsbandparkiet zich nog niet gevestigd heeft?

### Meer informatie
Onder de sectie resources/naslagwerk staan enkele .pdf files met artikels over de halsbandparkiet en de boomklever 

## Data verzamelen

### Waarnemingen.be
Waarnemingen.be is een onderdeel van observation.org, een wereldwijd biodiversiteitsplatform voor burgerwetenschap en monitoring, opgericht in 2004.
Dit is een samenwerking met onder andere Naturalis en Natuurpunt.

Hierop worden waarnemingen geplaatst vanuit verschillende bronnen, onder andere burgerobservatie, projecten, ....
Waarnemingen inbrengen is gemakkelijk via de website, mobiele applicaties voor smartphones of obsIdentify (°2017), waar je via automatische beeldherkenning waarnemingen kan loggen

### Initiële dataset
Initieel ben ik begonnen met een dataset op gbif die vrij beschikbaar is, nl. https://www.gbif.org/dataset/e7cbb0ed-04c6-44ce-ac86-ebe49f4efb28/metrics.
Hier stootte ik op volgende zaken
- panda's kan 12 000 000 waarnemingen niet aan. </br>
oplossing: grote datasets kunnen verwerkt worden met behulp van Dask (al had het gebruik van Polars ook soelaas kunnen brengen)
- uit de analyse van de dataset bleek dat deze niet toereikend was
    - De dataset bevat enkel Vlaanderen en Brussel, terwijl ik de oefening graag voor héél België wilde doen
    - Enkel data tem 2018, waardoor de laatste 6 jaar niet mee in de analyse zou zitten
    - Enkel inheemse vogels en geen exoten. Vermits de halsbandparkiet een exoot is, werd deze dataset in zijn geheel onbruikbaar

### Aanvraag bij natuurpuntdata
Ik contacteerde natuurpuntdata (natuurdata@natuurpunt.be) met de vraag of ik een geschikte dataset kon verkrijgen om deze analyse op uit te voeren.
Na enkele mails (met een gemiddelde responstijd van 10 dagen), werd ik zonder resultaat naar een nieuwe persoon doorverwezen. Terug bij af !!!

### Scraping van de data
Uiteindelijk ben ik de waarnemingen van de halsbandparkiet en de boomklever gaan scrapen op waarnemingen.be. Dit betrof ongeveer 277 000 waarnemingen van de boomklever en 97 000 voor de halsbandparkiet. 
Om niet teveel load op de server van waarnemingen.be te zetten haalde ik dit telkens op met tussen elke call een random delay van enkele seconden.
Het verzamelen van de data heeft zo ongeveer 1 maand in beslag genomen.

## Aannames
### Tijdsgebonden analyse: Het aandeel van onze vogelsoort in de observaties als maatstaf
- In onze statistische analyse verzamelen we jaarlijks steeds meer gegevens. Door de verbetering van de apps, automatische beeldherkenning wordt het steeds gemakkelijker om waarnemingen te loggen.
We kennen het totale aantal waarnemingen van vogels en zien dat deze stijgt in functie van de tijd.
In de tijdsgebonden analyse houden we geen rekening met het aantal waarnemingen van onze vogelsoorten, maar van het aandeel van de vogelsoort in het totaal aantal waarnemingen van datzelfde jaar.
Als het aandeel van een bepaalde vogelsoort stijgt, nemen we aan dat er daadwerkelijk meer vogels van die soort voorkomen.
- We maken de bemerking dat het aandeel van de waarnemingen van een soort niets wil zeggen over zijn effectieve aandeel in de vogelpopulatie. </br> Niet elke vogel is even gemakkelijk te spotten en te herkennen. De vogels die we dagdagelijks zien (kauwen, houtduiven, eksters, ...) worden in verhouding minder gelogd dan de minder frequentere soorten (ijsvogel, zanglijster, ...)

### We werken met observaties en niet met het aantal geobserveerde vogels
- we werken met # observaties en brengen het aantal vogels dat gezien zijn niet in rekening. De reden hiervoor is dat we in de data-analyse hebben gezien dat het aantal waargenomen vogels zich niet stabiel gedraagt en dat er serieuze uitschieters zijn. (zie cleaning_yearly_observations)
De ervaring met waarnemingen.be leert ook dat vele waarnemers (waaronder mezelf) niet de moeite doen om het aantal vogels mee te geven, en dan de standaarwaarde '1' wordt meegegeven.

### Validatie van de observaties wordt niet in rekening genomen
Van de observaties hebben 3% van de boomklevers en 22% van de halsbandparkieten een onbekende of nog niet beoordeelde validatie.
Vermits de halsbandparkiet en de boomklever gemakkelijk te identificeren vogels zijn, en niet snel te verwisselen met andere vogels is er geen rekening gehouden met de validatie status van de observatie. Er is besloten om ook de waarnemingen die niet beoordeeld zijn mee te nemen in de oefening.

### We verkiezen de unieke observators ipv het aantal waarnemingen
Er zijn verschillende soorten observators op waarnemingen.be. 
De personen die af en toe eens een waarneming loggen, maar er zijn ook personen die elke dag, elke vogel die ze zien loggen.
De waarnemingen van deze actieve loggers kunnen een vertekend beeld geven en de actieve loggers kunnen de waarnemingen beginnen domineren.
Daarom verkiezen we te werken met het aantal unieke observators voor een vogelsoort in plaats van het aantal waarnemingen.

## Structuur van de notebook
 
### 1_scraping
Het scrapen van alle data op waarnemingen.be. 
De enige cleaning die gebeurt is het samenbundelen van de verschillende scape sessies tot 1 csv-file en het verwijderen van dubbele data of data die achteraf werd verwijderd van waarnemingen.be
Het resultaat is te vinden in /scraped_data/cleaned

### 2_cleaning
Opschonen van de data.
De data wordt onder de folder "clean_data" opgeslagen in parquet-files. Deze hebben als voordeel dat we nadien steeds kunnen starten vanaf de parquet-files en dat de datatypes in deze file (in tegenstelling tot bij een csv-file) behouden blijven.

### 3_transformation
In deze stap wordt de clean data omgezet naar data die klaar is voor gebruik en analyse. 
De transformatie bestaat uit groeperen (per jaar, per locatie, per gemeente, ...), het berekenen van nieuwe waarden (bv. de groei).
De transformatie van de data wordt uitgevoerd in functie wat we nodig hebben bij de analyses. 
Het resultaat bevindt zich in de folder "gold". De data in deze folder bestaat enkel uit data die we effectief nodig hebben in de analyse. De analyse start steeds vanuit de data in de 'gold' folder.

### 4_Analyse
De verschillende analyses worden in deze sectie uitgevoerd. Analyses starten altijd vanaf de data gecreëerd in de transformatie sectie (3_transformation/gold).
Elke notebook bevat ook een uitgebreide en meer gedetailleerde conclusie. De gegenereerde plots worden bijgehouden onder de folder /plots van elke sectie

#### 1_belgium_yearly_evolution
- Als algemene conclusie kunnen we stellen dat zowel de boomklever als de halsbandparkiet het goed doen in België. De halsbandparkiet is nog steeds in opmars, al is de groeisnelheid aan het afnemen. De populatie van de boomklever begint te dalen. </br>We hebben voor meer dan 50 jaar data beschikbaar, maar de bulk van de observaties bevindt zich in de laatste 10 jaar.
- De laatste jaren is het merendeel van de waarnemingen afkomstig van 
    - ObsMapp (de android applicatie van waarnemingen.be)
    - via de waarnemingen.be site
    - iObs (de apple applicatie)
    - Obsidentify (via beeldherkenning)

#### 2_municipal
De boomklever is veel meer wijd verspreid is dan de halsbandparkiet.</br>
De halsbandparkiet bevindt zich vooral rond Brussel, Antwerpen en Kortrijk. Waarschijnlijk omdat rondom steden meer eten te vinden is, en de halsbandparkieten afhankelijk zijn van bijvoederen. En omdat ze profiteren van het hitte-effect van de stad. Halsbandparkieten verkiezen dan ook stadsparken als habitat.</br>
De boomklever bevindt zich zowat in het hele land, met uitzondering van een gedeelte van de kust en een regio in Luik.

#### 3_location
Om de correlatie tussen de concentratie van halsbandparkieten en de groei van de boomklever in kaart te brengen, concentreren we ons op de locaties die gespecifieerd zijn op waarnemingen.be.
Deze locaties zijn immers kleiner van oppervlakte dan de gemeentes. Zo kunnen we ook de lokale effecten in kaart brengen, dit is interessant omdat de halsbandparkiet in clusters lijkt voor te komen.

We merken initieel geen correlatie tussen de groei van de boomklevers en de concentratie van de halsbandparkieten. Als we echter enkel de locaties bestuderen waar zowel de boomklevers als de halsbandparkieten veel voorkomen, dan zien we wel een duidelijke correlatie. 
Waar de concentratie halsbandparkieten groot is, daar is er een daling in de boomklevers.

## Conclusie
De halsbandparkiet is een INVASIEVE exoot, want op plaatsen waar deze zich in grote concentraties bevinden, daar neemt de groei van de boomklever af.
Vermits het aandeel van de halsbandparkiet nog steeds aan het toenemen is, zal dit effect zich nog verder voortzetten.

## Afkortingen en definities
* bk: boomklever (boomklever en zijn ondersoorten)
* hp: halsbandparkiet
* pym: per jaarlijks miljoen waarnemingen

## Links
* [Eindwerk presentatie](https://docs.google.com/presentation/d/1t48EphVP-NK68GUzid34xKlaM8LB_F_9SuOflidjTzk/edit?usp=sharing)

## Opmerking van de auteur
* deze studie zou elk jaar kunnen herhaald worden. Het zou interessant zijn hoe de evolutie van de 2 soorten elkaar blijven beïnvloeden.
* Deze studie is gemakkelijk uitbreidbaar naar andere soorten. bv. wasbeer tov zwarte ooievaar