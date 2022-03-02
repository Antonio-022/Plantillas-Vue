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
        v-if="Mark1 == true"
        title="inicio"
        :coordinate="{
        latitude: latitudeI,
          longitude: longitudeI}"
      >
      </marker>
    <marker
    v-if="Mark2 == true"
        title="fin"
        :coordinate="{
          latitude: latitudeF,
          longitude: longitudeF
        }"
        draggable
      >

      </marker>
        <polyline
        v-if="routesCordenates != '' && Ena == true"
        :coordinates="routesCordenates"
            strokeColor="blue"
            :strokeWidth=4
            :geodesic="true"
            lineJoin="round"
            lineCap="round"
        />

    </map-view>

    <view class="c">

      <button :on-press="calcular" title="calcular la distancia"/>
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
import axios from 'axios';
import {Alert} from 'react-native'; 

export default {
  components: {
    MapView,
    Marker,
    Polyline,
  },
  data: function () {
    return {
      counter: 0,
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
        Mark1:false,
        Mark2:false,
        b1:false,
        b2:false,
      Ena:false,
      distancia:0,
    app_code:"dA6OVvngQ0Qb2M3JCaf8FA",
    app_id:"RyRKwcvkO5AXIwnVJ2fP",

      routesCordenates:[]
    };
  },
  methods: {
    onRegionChange(region) {
      this.coordinates = region;
    },
    onChange(event){
          this.mark = event.nativeEvent.coordinate;
          if(this.b1 == false )
          {
            this.routesCordenates = [];
            this.Ena=false;
            this.Mark1 = true;
            this.Mark2 = false;
            this.b1 = true;
            this.latitudeI = this.mark.latitude;
            this.longitudeI = this.mark.longitude;
            console.log(this.mark);
            console.log(this.coordinates);
            this.b2 = false;

            
          }
          else if(this.b2 == false )
          {
            this.Mark2 = true;
            this.b1 = false;
            this.b2 = true;
            this.latitudeF = this.mark.latitude;
            this.longitudeF = this.mark.longitude;
            console.log(this.mark);
            console.log(this.coordinates);
            this.Ena =true;
            
       axios.get('https://route.api.here.com/routing/7.2/calculateroute.json?app_id='+this.app_id+'&app_code='+this.app_code+'&waypoint0=geo!'+this.latitudeI+','+this.longitudeI+'&waypoint1=geo!'+this.latitudeF+','+this.longitudeF+'&mode=fastest;bicycle;traffic:disabled')
            .then((response) => (this.distancia = response.data.response.route[0].summary.distance))
        .then((data) => {
            console.log(data);
            this.distancia = Number(data);

        })
          .catch((error) => {
        console.log(error);
    })

           axios.get('https://route.api.here.com/routing/7.2/calculateroute.json?app_id='+this.app_id+'&app_code='+this.app_code+'&waypoint0=geo!'+this.latitudeI+','+this.longitudeI+'&waypoint1=geo!'+this.latitudeF+','+this.longitudeF+'&mode=fastest;bicycle;traffic:disabled')
            .then((response) => {
 
        response.data.response.route[0].leg[0].maneuver.map((m) => {
        this.routesCordenates.push({latitude: m.position.latitude, longitude: m.position.longitude});
      })
      console.log(this.routesCordenates);
     
    }).catch((error) => {
        console.log(error);
    })

      }
      },
      calcular()
      {
        

    
            Alert.alert( 'Distancia' , 'la distacia es : '+this.distancia+' mts' ,                 [                     { texto : 'Preguntarme más tarde' , onPress : () => console .log( 'Preguntarme más tarde presionado' )},                     { texto : ' Cancelar' , onPress : () => consola .log( 'Cancelar presionado' ), estilo : 'cancelar' },                     { texto : 'OK',
                
                onPress : () => console.log("click")
                
                }, 
                ], 
                { cancelable : false } 
            );
        }
 
  },
  beforeMount() {
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
              longitudeDelta: 0.002,
            });
 
          });
        }
      })
      .catch((err) => {
        console.log(err);
      });
  },
  mounted() {

  },
}

</script>