# CTTransit Real Time Bus Data for Trinity College

## Embedded on several pages
- http://commons.trincoll.edu/action-lab/transportation/
- http://commons.trincoll.edu/cli/transportation/
- http://www.trinfocafe.org/index.php/transportation/
- http://www.trincoll.edu/StudentLife/transportation/Pages/default.aspx

### CT Transit real-time bus location data feed

http://65.213.12.244/realtimefeed/vehicle/vehiclepositions.json

* NOT currently provided with https secure *

### Maintaining the map
1. Regularly download fresh GTFS data for Hartford from CTTransit Developers (https://www.cttransit.com/about/developers) whenever they update the file. Subscribe for alerts. Unzip the archive and place *routes.txt* and *trips.txt* files into **gtfs** folder.

1. Make sure that `route_id`s are up-to-date:
    * Go to `gtfs/routes.txt` and find all relevant bus routes near Trinity (37-39, 41, 61).
    * The first number in line is the `route_id` which is longer 5-digit code (example: 10073 route_id matches the 37-39 route)
    * In `index.html`, find the array variable **routesToDisplay** (as of 2018, around line 102) and make sure the ids listed there match the ones from *trips.txt*. Make sure to put them in single or double quotes (e.g. **'10073'** instead of **10073**).
    ```
    var routesToDisplay = ['10073' /*37-39*/, '10076' /*41*/, '10089' /*61*/]; // Updated Aug 28, 2018
    ```
1. Push changes to GitHub repo

**TO DO: update URL and instructions below after it works again **

1. The map also depends on a Python script to process the real-time feed. See `index.html` around line 293 reference to       
```
var jsonUrl = 'https://ct-transit.action-lab.org/';
```

which points to the action-lab.org ReclaimHosting file manager with this .htaccess script:

```
# DO NOT REMOVE. CLOUDLINUX PASSENGER CONFIGURATION BEGIN
PassengerAppRoot "/home/actionla/real-time-feed"
PassengerBaseURI "/"
PassengerPython "/home/actionla/virtualenv/real-time-feed/2.7/bin/python2.7"
# DO NOT REMOVE. CLOUDLINUX PASSENGER CONFIGURATION END
```

which runs a Python script in the virtual environment in action-lab.org ReclaimHosting account

![](img/python-app-screenshot.png)
