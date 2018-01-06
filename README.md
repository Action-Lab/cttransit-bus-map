# CTTransit Real Time Bus Data for Trinity College


### Maintaining the map
1. Download fresh GTFS data for Hartford from [CTTransit Developers](https://www.cttransit.com/about/developers) whenever it gets available. Unzip the archive and put all *.txt* files into **gtfs** folder.

1. Make sure that `route_id`s are up-to-date:
  * Go to `gtfs/trips.txt` and find all relevant bus routes. The first number in line is the `route_id`.
  * In `index.html`, find the array variable **routesToDisplay** (as of January 6, 2018, it is on line 102) and make sure the ids listed there match the ones from *trips.txt*. Make sure to put them in single or double quotes (e.g. **'1023'** instead of **1023**).
