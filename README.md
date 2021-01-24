# ufo-sightings
### Cleaned and organized NUFORC incidents from 2014-2020

### Intro
This .csv contains data scraped from the National UFO Reporting Center (NUFORC): http://www.nuforc.org/webreports.html

There are a number of versions of the NUFORC data floating around. This was intended to be an update to the popular dataset on Kaggle: https://www.kaggle.com/NUFORC/ufo-sightings which was originally compiled by Sigmund Axel here: https://github.com/planetsig/ufo-reports

This dataset starts where that version left off in 2014.  It is formatted and ordered so the two datasets can be unioned with minimal effort.

### New additions
**serial:** this is the end of the URL for the full text incident report and can serve as a unique identifier.

**link:** the link to the full text incident report on NUFORC's website.

**durationNumber and durationUnit** The number and time unit extracted from the original duration field using regex.  Included if the user wants to do their own time calculations or for further inspection/manipulation

### Geocoding details
For simplicity, the geocoding effort was limited to locations in the US.  Latitude and longitude was determined using this file
https://github.com/kelvins/US-Cities-Database, and the remaining missing locations were geocoded using an ESRI api via the geocoder python package (https://github.com/DenisCarriere/geocoder). This method didn't require an API key, used fuzzy matching, and didn't require a street address.  The resulting coordinates were then clipped using geopandas and a US border shapefile to remove any incorrect matches that were outside of the US.
