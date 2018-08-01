<template>
    <div id="map"
         :lat="lat"
         :lng="lng"
         :zoom="zoom"
         :markerLatLng="markerLatLng"
         :markerName="markerName"
    >
    </div>
</template>

<script>
import L from 'leaflet'

export default {
  name: 'ShivehMap',
  props: {
    lat: {
      type: Number,
      default: 33.1375
    },
    lng: {
      type: Number,
      default: 56.2170
    },
    zoom: {
      type: Number,
      default: 6
    },
    markerLatLng: {
      type: Array,
      default: ''
    },
    markerName: {
      type: Array,
      default: ''
    }
  },
  data () {
    return {
      map: null,
      tileLayer: null,
      layers: [{
        id: 0,
        name: 'markers',
        active: true,
        features: ''
      }]
    }
  },
  created () {
  },
  components: {
  },
  computed: {
  },
  mounted () {
    this.initMap()
    this.initLayers()
  },
  methods: {
    initMap () {
      this.map = L.map('map').setView([this.lat, this.lng], this.zoom)
      this.tileLayer = L.tileLayer.wms('http://map.ir/shiveh', {
        layers: 'Shiveh:ShivehGSLD256',
        format: 'image/png',
        attribution: '&copy; <a href="http://corp.map.ir">Map.ir</a> contributors'
      })
      this.tileLayer.addTo(this.map)
    },
    initLayers () {
      var markers = []
      if (this.markerLatLng.length > 0) {
        for (var i = 0; i < this.markerLatLng.length; i++) {
          markers[i] = {
            id: i,
            name: this.markerName[i],
            type: 'marker',
            coords: this.markerLatLng[i]
          }
        }
        this.layers[0].features = markers
      }
      this.layers.forEach((layer) => {
        var markerFeatures = layer.features
        markerFeatures.forEach((feature) => {
          feature.leafletObject = L.marker(feature.coords)
            .bindPopup(feature.name).addTo(this.map)
        })
      })
    }
  }
}
</script>

<style>
</style>
