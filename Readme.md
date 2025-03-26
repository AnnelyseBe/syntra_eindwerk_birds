# syntra_eindwerk_birds

## Inleiding
TODO
halsbandparkiet invasieve exoot, verhaal van vrijlating meli

### Opmars van de halsbandparkiet
De halsbandparkiet werd in Vlaanderen voor het eerst waargenomen in 1962 in Tervuren. Het eerste broedgeval dateert van 1966, toen een paar zes jongen grootbracht in een vervallen paviljoen in het Park van Tervuren. 
De eigenlijke opmars begon pas in 1974 toen in de Meli Zoo, gelegen op het plateau van de Heizel in Laken 40 tot 45 ex. werden vrijgelaten als speciale attractie voor de bezoekers.

We willen de opmars en de geleidelijke verspreiding van de halsbandparkiet in België in kaart brengen.

### Impact op de boomklevers
Halsbandparkieten zijn holenbroeders en geven de voorkeur aan oude nesten van de grote bonte specht. 

Net als halsbandparkieten hebben ook onze inheemse boomklevers een voorkeur voor oude nestgaten van de grote bonte specht. 
Halsbandparkieten starten eind november al met het verkennen van potentiële nestholten. Als de boomklevers in maart op zoek gaan naar een geschikte broedplaats, zijn de beste plaatsen vaak al bezet door halsbandparkieten, waardoor ze moeten uitwijken naar minderwaardige holtes. 
In gebieden waar veel halsbandparkieten zitten, zou het voor boomklevers moeilijk kunnen worden om een geschikte nestholte te vinden.

Op wikipedia vinden we terug dat, waar de halsbandparkiet terrein wint, de inheemse boomklever afneemt. In het ergste geval, zou een derde van de boomkleverpopulatie kunnen verdwijnen.

Maar kan dit ook aangetoond worden via de waarnemingen van boomklevers en halsbandparkieten op waarnemingen.be?
Is de evolutie van populatie van de boomklever hetzelfde in regio's waar de halsbandparkiet in opmars is, als waar de halsbandparkiet zich nog niet gevestigd heeft?

### Meer informatie
TODO links

## Data verzamelen
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
Na enkele mails (met een gemiddelde responstijd van 10 dagen), werd ik naar een nieuwe persoon doorverwezen. Terug bij ag

### Scraping van de data
Op de website waarnemingen.be bevat geregistreerde waarnemingen sinds 1970. 
Hiervoor ben ik de waarnemingen van de halsbandparkiet en boomklever gaan ophalen. 
Dit betrof ongeveer 277 000 waarnemingen van de boomklever en 97 000 voor de halsbandparkiet. 
Vermits dit veel data betreft en we niet teveel load op de server willen zetten, hebben we dit opgehaald met tussen elke call een random delay van enkele seconden.
Het verzamelen van de data heeft zo ongeveer 1 maand in beslag genomen.

## Aannames
- In onze statistische analyse verzamelen we jaarlijks meer gegevens doordat steeds meer mensen hun waarnemingen loggen op waarnemingen.be. We kennen het totale aantal waarnemingen van vogels en zien dat deze stijgt in functie van de tijd.
We gaan ervan uit dat het jaarlijkse aandeel van elke vogelsoort constant blijft als het aandeel in de populatie constant blijft. </br>Als het aandeel van een bepaalde vogelsoort stijgt, nemen we aan dat er daadwerkelijk meer vogels van die soort voorkomen.
- we werken met # observaties en brengen het aantal vogels dat gezien zijn niet in rekening. De reden hiervoor is dat we in de data-analyse hebben gezien dat het aantal waargenomen vogels zich niet stabiel gedraagt en dat er uitschieters zijn. (zie cleaning_yearly_observations)
De ervaring met waarnemingen.be leert ook dat vele waarnemers niet de moeite doen om het aantal vogels mee te geven, en dan de standaarwaarde '1' wordt meegegeven.




