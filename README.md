# Map Visualization Tool

A self-sufficient interactive map visualizer integrated with charting and graphing tools for depicting geolocational data. 

### Feature List

- **Zoom Controls**: Zoom in and out to any level.
- **Layer Controls**: Manage and toggle between multiple layers within the same map simultaneously.
- **Search**: Automatically locate and pan to a requisite region.
- **Data Visualization**: View charts, graphs, and tabular data pertaining to a select region by clicking over it.
- **Choropleths**: Regions shaded with color scales based on requsite statistics.
- **Alter Metadata**: Dynamically change map properties using the right click menu. 
- **Heatmaps**: Depict highly dense geospatial data.
- **Range Slider**: Depict time-bound data over customizable periods.

## Parent Library - Leaflet.js 

[Leaflet](https://leafletjs.com) is the leading open-source JavaScript library for mobile-friendly interactive maps. 
Used as the parent library for all map based interactions. Since it is exclusively a map API and not a full-fledged engine like Google Maps, 
it requires sourcing map images from third-party tile repositories such as [OpenStreetMaps](https://www.openstreetmap.org/).

### Comparison between different open-sourced mapping libraries

|                         | Leaflet                    | Cesium               | Mapbox-GL             | OpenLayers        |
|-------------------------|----------------------------|----------------------|-----------------------|-------------------|
| Github Stars            | 31,135                     | 7,273                | 7,679                 | 8,225             |
| Github Issues           | 695                        | 1,165                | 835                   | 118               |
| Documentation           | Extensive                  | Limited              | Extensive             | Extensive         |
| Community Support       | Highly Active              | Active               | Fairly Active         | Fairly Active     |
| Ease of  implementation | Fast and  extremely simple | Fairly easy          | APIKey-Based  Access  | High Complexity   |
| Feature Richness        | Major use-cases only       | Major use-cases only | High, Freemium  model | High              |
| Resource Size           | Light (39.9 kB)            | Heavy (867.9 kB)     | Heavy (218.9 kB)      | Medium (151.7 kB) |


Leaflet supports a large number of support plugins, the ones included in the project are mentioned below along with their use cases.

- [Leaflet-choropleth](https://github.com/timwis/leaflet-choropleth): Color Scaled Maps for stastically varied regions
- [Leaflet.heat](https://github.com/Leaflet/Leaflet.heat): Heatmaps
- [Leaflet-search](https://github.com/stefanocudini/leaflet-search): Multi-layer Region Finder 
- [Leaflet-omnivore](https://github.com/mapbox/leaflet-omnivore): Dataset conversion (CSV/KML/TopoJSON - GeoJSON)
- [Leaflet.EasyButton](https://github.com/CliffCloud/Leaflet.EasyButton): Interactive map buttons
- [Leaflet.contextmenu](https://github.com/aratcliffe/Leaflet.contextmenu): On-click interactive menus
- [LeafletSlider](https://github.com/dwilhelm89/LeafletSlider): Time-bound data representation


## Dataset Formats

Leaflet accepts a specific data format - [GeoJSON](https://en.wikipedia.org/wiki/GeoJSON) for generating layers, which in turn allows two kinds of geometries - 
Points(for location-specific data) and Polygons (for region-specific data). Any dataset needs to converted to the GeoJSON format for enable parsing. 

### Point geometries

These represent singular instances which signify the occurence of an event at a given location. Data of this kind is usually available in the CSV format, with ***Latitude*** 
and ***Longitude** being mandatory attributes. Any such file can easily be converted to a GeoJSON format using open-sourced tools like 
[CSV2GEOJSON](https://odileeds.github.io/CSV2GeoJSON/).

### Polygon geometries

These represent the boundaries of a certain geographical region such as a county/borough, city, state, or a country. This data is either available readily in the 
GeoJSON format, or needs to be converted from TopoJSON, or a combination of .SHP (shapefile) and .DBF (database) files. While TopoJSON files can easily be converted 
leaflet-omnivore, SHP and DBF files need to be feeded into a tool like [mapshaper](https://mapshaper.org) to generate the resultant GeoJSON.

Example sources - [DIVA-GIS](https://diva-gis.org/data), [Natural Earth](https://naturalearthdata.com/downloads/), and most administrative government repositories
like New York City's [website](https://data.cityofnewyork.us).


## Tile Repository: OpenStreetMap

Leaflet requires sourcing tiles(map images) from external tile repositories like OpenStreetMap, which in turn requires communication over the internet. However, 
for creating a self-sufficient map which can work offline, we need to download all required tiles to the local repository which is achieved using the [Offline Map Maker](http://www.allmapsoft.com/omm/) software. 

Since the number of such tiles (images) can be pretty large, we limit our zoom and bounding box pan levels to appropriate and requisite values.

