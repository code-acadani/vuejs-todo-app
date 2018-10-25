<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div id="map"></div>
  </div>
</template>

<style>
  /* Always set the map height explicitly to define the size of the div
   * element that contains the map. */
  #map {
    height: 500px;
  }
</style>

<script>
export default {
  data: function() {
    return {};
  },
  methods: {},
  mounted: function() {
  	var map;
	  map = new google.maps.Map(document.getElementById('map'), {
	    center: { lat: 37.773972, lng: -122.431297 },
	    zoom: 11
	  });
  },
  computed: {}
};
</script>