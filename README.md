Leaflet GeoCSV
==============

[English](#why-geocsv): [Leaflet](https://github.com/Leaflet/Leaflet) plugin for loading a CSV file as geoJSON layer.


Why GeoCSV?
-----------

* **Ease of use**: A CSV (comma-separated values) file is a simple and open file format that stores tabular data in
plain-text form. Virtually all spreadsheet and database software can import/export this file format.

* **Save bandwidth**: When used to display markers, GeoJSON files can be up to four times as large as a CSV file
containing the same information. This plugin provides the ability to download a CSV file that is then parsed into a
GeoJSON document on the client side, saving you bandwidth and reducing load times. In similar scenarios, we recommend
using GeoCSV together with [MarkerCluster](//github.com/danzel/leaflet.markercluster) as in the
[Bankia Offices Map Example](//joker-x.github.com/Leaflet.geoCSV/example/bankia/index.html).


Download
--------

*  Plugin only (2.4k, uncompressed): [leaflet.geocsv.js](leaflet.geocsv.js)

*  Full Repository (includes plugin, all prerequisites and examples): [.ZIP](https://github.com/joker-x/Leaflet.geoCSV/archive/master.zip) or [.TAR.GZ](https://github.com/joker-x/Leaflet.geoCSV/archive/master.tar.gz)


Options
-------

GeoCSV inherits the configuration options and methods of its parent object, the [GeoJSON](//leafletjs.com/reference.html#geojson) layer, and further defines the following of its own:

* **titles**: An array of field titles in the same order in which they appear within the CSV file. GeoCSV only requires the presence of two field titles, `lat` and `lng` (latitude and longitude, respectively); all others field titles are permitted, omitting spaces, capitalization, accent characters, etc. By default, `titles: ['lat', 'lng', 'popup']`

* **latitudeTitle**: The title used for the latitude value of the feature. By default, `latitudeTitle: 'lat'`.

* **longitudeTitle**: The title used for the longitude value of the feature. By default, `longitudeTitle: 'lng'`.

* **lineSeparator**: The string delimiting lines within the CSV file (between each GeoJSON feature). By default, `lineSeparator: '\n'`.

* **fieldSeparator**: The string delimiting individual fields within each feature. By default, `fieldSeparator: ';'`.

*  **deleteDoubleQuotes**: A boolean indicating if double quotes surrounding individual field values should be removed. By default, `true`.

* **firstLineTitles**: A boolean indicating if the first line of the CSV file contains field titles. If set to false, the plugin will ignore the `titles` configuration option. By default, `false`.


Methods
-------

*  **getPropertyTitle(** propertyName **)**: When passed a property name (string), returns the associated property title.

*  **getPropertyName(** propertyTitle **)**: When passed a property title (string), returns the associated property name.

Use
---

1. Include the plugin JavaScript file after leaflet.js: `<script src="leaflet.geocsv.js"></script>`

2. Create a GeoCSV layer by instantiating the class or calling `L.geoCsv()`. Where `csvFileContents` is the content of a CSV file and `options` is an object literal as described in the previous section: `var csvLayer = L.geoCsv(csvFileContents, options);`

An example, using jQuery to read a CSV file, and adding a GeoCSV layer to a map:

```js
(function() {
  'use strict';

  var map = L.map('mapContainer');

  $.get('data.csv', function(csvContents) {
    var geoLayer = L.geoCsv(csvContents, {firstLineTitles: true, fieldSeparator: ','});
    map.addLayer(geoLayer);
  });
});
```


Examples
--------

Complete examples can be found within the `examples` subdirectory of the repository:

*  [Configuration Options Test](//joker-x.github.com/Leaflet.geoCSV/example/options-test/index.html)

*  [Data Passing Through the URL](//joker-x.github.com/Leaflet.geoCSV/example/from-url/index.html)

*  [Bankia Offices (GeoCSV + MarkerCluster)](//joker-x.github.com/Leaflet.geoCSV/example/bankia/index.html)

