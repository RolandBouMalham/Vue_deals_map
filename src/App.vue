<template>
  <DealsMap msg="Welcome to Your Vue.js App" v-bind:UK_deals="UK_sum"/>
</template>

<script>
import DealsMap from './components/DealsMap.vue'

export default {
  name: 'App',
  components: {
    DealsMap
  }
}

</script>

<style>
*,
*::before,
*::after {
    padding: 0;
    margin: 0;
    box-sizing: border-box;

}

body {
    box-sizing: inherit;
    font-family: 'Rubik', sans-serif;
    font-size: 18px;
    color: black;
}

h3{
  display:inline;
}

.map-container {
    background-color: black;
    min-height: 80vh;
}

.circle {
  border-radius: 50%;
  width: 34px;
  height: 34px;
  padding: 10px;
  display: inline-block;
  border: 0px;
  color: white;
  text-align:left;
  font: 20px Arial, sans-serif;
}

.split {
  height: 100%;
  width: 25%;
  position: fixed;
  z-index: 1;
  top: 280px;
  overflow-x: hidden;
  padding-top: 0;
}

.first {
  left: 0;
}

.second{
  right: 50%;
}

.third{
  left: 50%;
}

.fourth{
  right: 0;
}

.centered {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
}

.centered img {
  width: 150px;
  border-radius: 50%;
}

.button{
  padding: 0;
  border: none;
  background: none;
  font-size: 18px;
  color:rgb(26, 26, 220);
  text-align:right;
  display: inline;
  float: right;
}

.button:hover{
  cursor: pointer;
  color :rgb(90, 90, 186)
}
</style>
