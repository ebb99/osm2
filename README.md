<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="de" lang="de-de">
<head>
  <title>Map | Testanwendung</title>
  <meta http-equiv="content-type" content="text/html; charset=UTF-8" />
  <script src="https://openlayers.org/api/OpenLayers.js"></script>
  <script src="https://openstreetmap.org/openlayers/OpenStreetMap.js"></script>
  <script type="text/javascript">
    function drawmap() {
      var lon = 13.457619, lat = 52.515275, zoom = 14;
      map = new OpenLayers.Map('map', {
        projection: new OpenLayers.Projection("EPSG:900913"),
        displayProjection: new OpenLayers.Projection("EPSG:4326"),
        controls: [new OpenLayers.Control.Navigation(),
                   new OpenLayers.Control.LayerSwitcher(),
                   new OpenLayers.Control.PanZoomBar()],
        maxExtent: new OpenLayers.Bounds(-20037508.34,-20037508.34,
                                          20037508.34, 20037508.34),
        numZoomLevels: 18,
        units: 'meters'
      });
      var layer_mapnik = new OpenLayers.Layer.OSM.Mapnik("Mapnik");
      var layer_markers = new OpenLayers.Layer.Markers("Address", {
        projection: new OpenLayers.Projection("EPSG:4326"),
        visibility: true, displayInLayerSwitcher: false
      });
      map.addLayers([layer_mapnik, layer_markers]);
      map.setCenter(new OpenLayers.LonLat(lon, lat), zoom);
      addMarker(layer_markers, lon, lat, "<b>Beispielort</b>");
    }
  </script>
</head>
<body onload="drawmap();">
  <div id="map" style="width:100%; height:600px;"></div>
</body>
</html>
