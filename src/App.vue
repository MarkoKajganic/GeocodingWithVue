<template>
  <div id="app">
    <img src="./assets/logo.png">
    <geocoding></geocoding>
  </div>
 
</template>

<script>
import Geocoding from './components/Geocoding'

export default {
  name: 'App',
  components: {
    Geocoding
  }
}
</script>

<style>
#app {
  text-align: center;
  margin-top: 20px;
}
</style>
