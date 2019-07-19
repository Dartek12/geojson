# Geojson

Utilities to work with geojson data in Dart.

## Example

   ```dart
   import 'dart:io';
   import 'package:geojson/geojson.dart';

   void main() async {
     polygons(file);
     lines(file);
   }

   void polygons() async {
     final file = File("lakes_of_europe.geojson");
     final geoSeries = await geoSerieFromFile(file, nameProperty: "label");
     for (final geoSerie in geoSeries) {
       print("${geoSerie.name}: ${geoSerie.geoPoints.length} geopoints");
     }
   }

   void lines() async {
     final file = File("railroads_of_north_america.geojson");
     final geoSeries = await geoSerieFromFile(file, nameProperty: "continent");
     for (final geoSerie in geoSeries) {
       print("${geoSerie.name}: ${geoSerie.geoPoints.length} geopoints");
     }
   }
   ```

## Api

`geoSerieFromFile`: create geoseries from a geojson file. Parameters:

- `file`: the file to load, required
- `nameProperty`: the property used for the geoserie name, default "name"
- `type`: the geoserie type, infered from the file if not provided
- `verbose`: print data if true
