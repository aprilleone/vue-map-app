<template>
  <div id="mapContainer" class="basemap"></div>
</template>

<script>
import mapboxgl from "mapbox-gl";

export default {
  name: "BaseMap",
  data() {
    return {
      accessToken: 'pk.eyJ1IjoiYXByaWxsZW9uZSIsImEiOiJja3U2MmU1YXAxcGRhMnhtcGczcnlubXM3In0.PB-PbtTzjIBCKJYOxJ7Pdg',
    };
  },
  mounted() {
    mapboxgl.accessToken = this.accessToken;

    let map = new mapboxgl.Map({
        container: "mapContainer",
        style: "mapbox://styles/mapbox/satellite-streets-v11",

        center: [-116.94433365793185, 36.45481045789571], // notice it's long/lat to match GeoJSON
        zoom: 16,
        // pitch: 60,
        // bearing: -20,
    //   maxBounds: [
    //     [103.6, 1.1704753],
    //     [104.1, 1.4754753],
    //   ],
    });
    const nav = new mapboxgl.NavigationControl();
    map.addControl(nav, "top-right");

    const geolocate = new mapboxgl.GeolocateControl({
        positionOptions: {
            enableHighAccuracy: true
        },
        trackUserLocation: true
    });

    map.addControl(geolocate, "top-right")
    new mapboxgl.Marker().setLngLat([-116.94433365793185, 36.45481045789571]).addTo(map);
    const scale = new mapboxgl.ScaleControl({
    maxWidth: 80,
    unit: 'metric'
    });
    map.addControl(scale);
 
  },
  
};
</script>

<style  scoped>
.basemap {
  width: 90%;
  height: 1000px;
  margin:auto;
}
</style>