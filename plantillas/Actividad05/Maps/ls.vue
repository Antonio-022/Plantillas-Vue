<template>
  <view class="container">
    <map-view
      class="map"
      :initial-region="coordinates"
      ref="mapa"
      :zoomControlEnabled="true"
      :loadingEnabled="true"
      :onRegionChangeComplete="onRegionChange"
      :on-press="onChange"
    >
      <marker
     
        title="inicio"
        :coordinate="{
        latitude: latitudeI,
          longitude: longitudeI}"
      >
      </marker>
    <marker
        title="fin"
        :coordinate="{
          latitude: latitudeF,
          longitude: longitudeF
        }"
        draggable
      >

      </marker>
        <polyline
        :coordinates="[{
          latitude: latitudeI,
        longitude: longitudeI},{
        latitude: latitudeF,
        longitude: longitudeF
        }
        ]"
            strokeColor="blue"
            :strokeWidth=4
        />

    </map-view>

    <view class="c">

      <button title="calcular la distancia"/>
    </view>
  </view>
</template>
<style>

.container {
  flex: 1;
  background-color: #fff;
  align-items: center;
}
.map {
  width: 100%;
  height: 95%;
}
.c {
  height: 100%;
  width: 100%;
}
</style>
<script>
import MapView, { Marker, Polyline } from "react-native-maps";
import * as Location from "expo-location";

export default {
  components: {
    MapView,
    Marker,
    Polyline,
  },
  data: function () {
    return {
      coordinates: {
        latitude: 12.91074,
        longitude: 77.5996363,
        latitudeDelta: 0.0922,
        longitudeDelta: 0.0421,
      },

        latitudeI: -17.5994623,
        longitudeI: -63.1186431,


        latitudeF: -17.597858,
        longitudeF: -63.115979,

  
  
      locationText: "",
    };
  },
  methods: {
    onRegionChange(region) {
      this.coordinates = region;
    },
    onChange(){
          if(this.coordinates.latitude != this.latitudeI);
          {
            this.latitudeI = this.coordinates.latitude;
            this.longitudeI = this.coordinates.longitude;
            }
      }
 
  },
  mounted() {
    Location.requestForegroundPermissionsAsync()
      .then((status) => {
        if (!status.granted) {
          this.errorMessage = "Permission to access location was denied";
        } else if (status.granted) {
          Location.getCurrentPositionAsync({}).then((location) => {
            this.$refs.mapa.animateToRegion({
              latitude: location.coords.latitude,
              longitude: location.coords.longitude,
              latitudeDelta: 0.001,
              longitudeDelta: 0.05,
            });
            

          });
        }
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>