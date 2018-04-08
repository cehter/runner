<template lang="html">
  <div class="wrapper">
    <div id="map" />
    <table>
      <tr>
        <td>Distance:</td>
        <td>{{distance}}km</td>
      </tr>
      <tr>
        <td>Duration:</td>
        <td>{{durationMoving}}m</td>
      </tr>     
        <tr v->
        <td>Pace:</td>
        <td>{{pace}}min</td>
      </tr >
    </table>
    <!-- <ul class="dataList">
      <li>Distanz: {{distance}}</li>
      <li>Start: {{start}} </li>
      <li>End: {{end}}</li>
      <li>Dauer bewerbung: {{durationMoving}}</li>
      <li>Dauer gesamt: {{durationTotal}}</li>
      <li>speed: {{speed}}</li>
      <li>pace: {{pace}}</li>
      <li>elevationGain : {{elevationGain}}</li>
      <li>elevationLoss : {{elevationLoss}}</li>
    </ul> -->
  </div>
</template>

<script>
import 'leaflet'
import '../assets/lib/leaflet-gpx/gpx';

import startIconUrl from './../assets/lib/leaflet-gpx/pin-icon-start.png';
import endIconUrl from './../assets/lib/leaflet-gpx/pin-icon-end.png';
import shadowUrl from './../assets/lib/leaflet-gpx/pin-shadow.png';
import gpx from 'raw-loader!./../assets/test.gpx';

const L = window.L;
export default {
  data() {
    return {
      distance: null,
      start: null,
      end: null,
      durationMoving: null,
      durationTotal: null,
      speed: null,
      pace: null,
      elevationGain: null,
      elevationLoss: null
    }
  },
  mounted() {

    const map = L.map('map').setView([37.4501001, -121.9107704], 4)
    let distance = null;
    
    L.tileLayer('http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: 'Map data &copy; <a href="http://www.osm.org">OpenStreetMap</a>'
    }).addTo(map);

    new L.GPX(gpx, {
      async: true,
      marker_options: {
        startIconUrl: startIconUrl,
        endIconUrl: endIconUrl,
      }
    }).on('loaded', (e) => {
      const target = e.target;
      this.distance = Math.round(target.get_distance() / 100) / 10;
      this.durationMoving = target.get_duration_string_iso(target.get_moving_time());
      this.durationTotal = target.get_duration_string_iso(target.get_total_time());
      this.start = target.get_start_time();
      this.end = target.get_end_time();
      this.speed = target.get_total_speed();
      this.pace = target.get_moving_pace();
      this.elevationGain = target.get_elevation_gain();
      this.elevationLoss = target.get_elevation_loss();
      map.fitBounds(target.getBounds());
    }).addTo(map);

    this.map = map
  }
}
</script>

<style>
    @import "~leaflet/dist/leaflet.css";
    .wrapper {
      display: flex;
    }
    #map {
      width: 400px;
      height: 400px;
      display: block;
    }
    .dataList{
      list-style: none;
    } 
</style>