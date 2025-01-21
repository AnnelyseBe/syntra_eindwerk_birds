# syntra_eindwerk_birds
studie invasieve exoten met dataset https://www.gbif.org/dataset/e7cbb0ed-04c6-44ce-ac86-ebe49f4efb28/metrics (natuurdata@natuurpunt.be)

https://www.natuurpunt.be/soorten/vogels/halsbandparkiet#paragraph--layout_2_col--2543 -> boomklevers die lijden onder de halsbandparkieten
https://www.vrt.be/vrtnws/nl/2024/11/05/wasberen-in-opmars-in-limburg-gisteren-nog-eentje-gevangen-in-b/ (bosuilen, oehoe, zwarte ooievaar, wouw)

# ToDo
Scale for Large Data: If your raw file has millions of rows, use tools like Dask (eenvoudig, op 1 machine) or PySpark (complexer, interessant voor naar clusters te gaan) to handle the full dataset efficiently.

# problemen
dataset te groot voor pandas -> 12 000 000 crash
dataset bevat geen exoten :-), dataset niet recent

# oplossingen 
webscraping lijkt mogelijk (via incognito en niet ingelogged kan ik nog de resulaten verkrijgen)
3900 pagina's https://waarnemingen.be/species/119/observations/?date_after=1970-01-15&date_before=2025-01-14&page={}'


