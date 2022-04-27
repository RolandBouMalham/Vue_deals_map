<template>
<div class="body">
  <h3>Deals by country </h3>
  <button id="btn-id" v-on:click="viewReport" class="button"><b>View Report</b></button>
  <!-- Map -->
    <div id="mapid" class="map-container"></div>
  <div class="split first">
      <div class="centered">
        <div class="circle column" style="background: #d5e733;">1</div>
        <span>UK </span>
        <span style="font-size: 12px;" id="numb_of_UK_deals"></span>
      </div>
    </div>
    <div class="split second">
      <div class="centered">
        <div class="circle column"  style="background: rgb(77, 199, 84);">2</div>
        <span>USA </span>
        <span style="font-size: 12px;" id="numb_of_US_deals"></span>
      </div>
    </div>
    <div class="split third">
      <div class="centered">
        <div class="circle column" style="background: rgb(76, 76, 230);">3</div>
        <span>India </span>
        <span style="font-size: 12px;" id="numb_of_India_deals"></span>
      </div>
    </div>
    <div class="split fourth">
      <div class="centered">
        <div class="circle column" style="background: blue;">4</div>
        <span>Australia </span>
        <span style="font-size: 12px;" id="numb_of_Australia_deals"></span>
      </div>
    </div>
</div>
</template>

<script>
import * as L from 'leaflet';
import { onMounted } from "vue";

let UK_cities = {
    London:8,
    Liverpool:4,
    Leeds:1,
    Manchester:2,
    Leichester:1,
    Brithon_and_Hove:1,
    Norwich:2,
    Sheffield:1,
}

let USA_cities = {
    Lancaster:2,
    Garden_Grove:1,
    Glendale:1,
    Worchester:1,
    Norfolk:1,
    Madison:1,
    Orlando:2,
}

let India_cities = {
    Mumbai:5,
    Delhi:3,
    Jaipur:2,
    Surat:2,
    Kanpur:3,
}

let Australia_cities = {
    Sydney:6,
    Melbourne:3,
    Adelaide:2,
    Townsville:1,
}

var UK_deals = UK_cities.London + UK_cities.Liverpool + UK_cities.Leeds + UK_cities.Manchester + UK_cities.Leichester + UK_cities.Brithon_and_Hove + UK_cities.Norwich + UK_cities.Sheffield;
var US_deals = USA_cities.Lancaster + USA_cities.Garden_Grove + USA_cities.Glendale + USA_cities.Worchester + USA_cities.Norfolk + USA_cities.Madison + USA_cities.Orlando;
var India_deals = India_cities.Mumbai + India_cities.Delhi + India_cities.Jaipur + India_cities.Surat + India_cities.Kanpur;
var Australia_deals = Australia_cities.Sydney + Australia_cities.Melbourne + Australia_cities.Adelaide + Australia_cities.Townsville;




export default {
  name: 'DealsMap',
  props: {
    data: String,
    UK_deals : Number,
  }, methods:{
    viewReport()
    {
      alert(
        'UK deals:' + '\r\n' +
        JSON.stringify(UK_cities,null, 4) + '\r\n' +
        'USA deals:' + '\r\n' +
        JSON.stringify(USA_cities,null, 4)
      );

      alert(
        'India deals:' + '\r\n' +
        JSON.stringify(India_cities,null, 4) + '\r\n' +
        'Australia deals:' + '\r\n' +
        JSON.stringify(Australia_cities,null, 4)
      );
    },
  },
  setup(){
    // create map variable
    let map; 
    // mounted lifecycle hook, creates the map
    onMounted(() => {
      map = L.map("mapid").setView([30, 50], 2);
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
    }).addTo(map);
    //Adding markers to the map:
    L .marker([-20.473469, 130.0124], {title:"Australia"}).addTo(map);
    L .marker([28.66, 72], {title:"India"}).addTo(map);
    L .marker([51.509865, -0.118092], {title:"UK"}).addTo(map);
    L .marker([50, -110], {title:"USA"}).addTo(map).bindPopup('Hover over each marker to see country name').openPopup();
    });
  },
}
window.onload = function() {
  document.getElementById("numb_of_UK_deals").innerHTML= UK_deals;
  document.getElementById("numb_of_US_deals").innerHTML= US_deals;
  document.getElementById("numb_of_India_deals").innerHTML= India_deals;
  document.getElementById("numb_of_Australia_deals").innerHTML= Australia_deals;

}
</script>
