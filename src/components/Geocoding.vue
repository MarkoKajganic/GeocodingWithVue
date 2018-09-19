<template>
    <div class="geocoding">

        <h1> {{ hello }} </h1>
        <input v-model="address" placeholder="enter adress here">
        <p>Address is: {{ address }}</p>
        <button v-on:click="findCoordinates(address)"> Search </button>

        <div v-if="location.results!=undefined">
            <p> Latitude: {{ location.results[0].geometry.location.lat }} </p>
            <p> Longitude: {{ location.results[0].geometry.location.lng }} </p>
        </div>

    </div>
</template>

<script>
export default {
  name: "geocoding",
  data() {
    return {
      hello: "Geocoding with Vue.js",
      address: "",
      location: Object,
      findCoordinates: function(address) {
        let urlAddress = address.split(" ").join("+");
        this.$http.get(`https://maps.googleapis.com/maps/api/geocode/json?address=${urlAddress}&key=AIzaSyDm9OtQtz0Y_w_ROiwnjjJN9D7_EcBCAtA`)
          .then(function(response) {
            this.location = response.data;
          });
      }
    };
  }
};
</script>

<style>
p {
  font-size: 1.5em;
}

input {
  font-size: 1.5em;
}

button {
  padding: 15px 25px;
  font-size: 24px;
  text-align: center;
  cursor: pointer;
  outline: none;
  color: #fff;
  background-color: #4caf50;
  border: none;
  border-radius: 15px;
}
</style>
