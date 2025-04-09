- [ ] Scaling
  - [ ] Hernoemen naar Transformation
  - [ ] de parquet observations_yearly_scaled mag weg (wordt niet verder gebruikt)
  - [ ] tabellen - https://docs.google.com/spreadsheets/d/1KZRyxxaCpyHaAHIkvHORNbo0aXazWaCckck3ii-xcSY/edit?gid=0#gid=0
    - [ ] observations_boomklever (scaled veld -> observations = 1, observations_pym (per yearly million))
    - [ ] observations_halsbandparkiet

- [ ] 6_regional_investigation
    - [ ] per gemeente, de stijging in 2024 tov de laatste 5 en de laatste 10 jaar
        - [x] dit wil zeggen dat we de scaled_data van de laatste 10 jaar ook nog even moeten meenemen en pas later moeten filteren in onze folium kaart
        - [x]iets generieker maken en pas op het einde halsbandparkiet en boomklever mergen
        - [x] we moeten nog een rollend gemiddelde van 5 jaar meegeven en de stijging van het rollend gemiddelde berekenen over de laatste 5 jaar
        - [X] visueel de correlatie stijging halsbandparkiet (X-as), boomklever (Y-as)
            - per gemeente gegroepeerd
            - aantal scaled waarnemingen (of zelfs unieke observers) geeft de grootte van onze bol
            - voorbeelden
                - https://matplotlib.org/stable/gallery/lines_bars_and_markers/scatter_demo2.html#sphx-glr-gallery-lines-bars-and-markers-scatter-demo2-py
                - https://matplotlib.org/stable/gallery/lines_bars_and_markers/scatter_with_legend.html
            - [ ] fix, we willen observers per km2 
        - [X] visueel de correlatie halsbandparkiet (X-as) waarnemingen/km2, boomklever (Y-as) (groei)

- [ ] indien nog tijd. De locations_general samenvoegen tot 1 locations_general_clean. Dan nog eens de 5_ webscraping en cleaning van de details
- [ ] indien nog tijd. Heatmap timelapse

