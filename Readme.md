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
Hiervoor ben ik de waarnemingen van de halsbandparkiet en boomklever gaan ophalen. Vermits dit ging over 



    - probleem: 12 000 000 waarnemingen -> panda's kan dit niet aan
    Oplossing: Scale for Large Data: If your raw file has millions of rows, use tools like Dask (eenvoudig, op 1 machine) or PySpark (complexer, interessant voor naar clusters te gaan) to handle the full dataset efficiently.
    - probleem na gebruik dask. Dataset is niet toereikend. Geen exoten (en dit is het onderwerk van de studie), enkel vogels (geen wasbeer), enkel Vlaanderen en Brussel (wasberen vooral in ardennen), slecht data tem 2018
    - ik zou ook via polars kunnen werken ipv pandas

aanvraag bij natuurpuntdata
- 10-jan-2025 PISTE specifieke data aanvragen bij Natuurpuntdata mail gestuurd naar natuurdata@natuurpunt.be om te kijken of ik mijn gewenste data zou kunnen verkrijgen
    - 20 januari antwoord, met wat extra vragen, waar ik de dag nadien op heb geantwoord

scraping -> 1 maand (15 jan - 17 feb)
- 15-jan-2025 PISTE SCRAPEN effectief begonnen aan het scrapen voor case halsbandparkiet, boomklever
    - ik besef dat dit lang gaat duren als ik de waarnemingen elk afzonderlijk moet scrapen
- 17-feb-2025 gedaan met scrapen



