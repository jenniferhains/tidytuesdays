# Create interactive site maps

```r
library(tidyverse)
library(leaflet)


sites <- read_csv('https://raw.githubusercontent.com/MPCA-air/aqi-watch/master/data-raw/locations.csv')


# Map sites
leaflet(sites) %>%
   addMarkers()


# Add basemap
leaflet(sites) %>%
  addProviderTiles(providers$CartoDB) %>%
  addMarkers()


# Add popup info & Darkness
leaflet(sites) %>%
  addProviderTiles(providers$CartoDB.DarkMatter) %>%
  addMarkers(popup = ~`Site Name`)


# Add label only to Fargo
leaflet(sites) %>%
  addProviderTiles(providers$CartoDB.Voyager) %>%
  addMarkers(popup = ~`Site Name`) %>%
  addPopups(data  = filter(sites, `Site Name` == "Fargo NW"),
            popup = ~`Site Name`)



# Add color markers
leaflet(sites) %>%
  addProviderTiles(providers$CartoDB.Voyager) %>%
  addCircleMarkers(popup = ~`Site Name`) %>%
```


