# 🗺️ DSNC Bounds Checker

A browser-based tool to check whether a given address falls within the Davis Square Neighborhood Council (DSNC) boundary.

Simply open `bounds_checker.html` in a browser (no backend required). Enter an address and see if it's within DSNC bounds!

Most importantly, there is no server. Works entirely on the front end via CDNs and some suspicious github hosting of the Neighborhood shape file.

## Technologies Used

- [Leaflet.js](https://leafletjs.com/) (Map rendering)
- [shpjs](https://github.com/calvinmetcalf/shapefile-js) (Shapefile → GeoJSON)
- [Turf.js](https://turfjs.org/) (Spatial analysis)
- [Nominatim](https://nominatim.org/) (Address → lat/lon)

## How It Works

1. A zipped shapefile of Somerville neighborhoods is loaded and parsed via `shpjs`.
2. The Davis Square feature (by index) is extracted and drawn on the map.
3. A Turf.js buffer (0.5 miles as defined by bylaws) is computed around the neighborhood polygon and also shown.
4. When a user enters an address:
   - It is geocoded via Nominatim
   - A point is constructed and checked for intersection with the Davis polygon
   - The result is displayed to the user
