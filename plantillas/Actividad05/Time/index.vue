<template>
  <native-base-provider>
    <view class="container" h="100%" w="100%" bg="info.700">
      <center>
        <text font-size="35px" mt="5" color="light.50">Clima</text>
        <text font-size="15px" mt="5" mr="40%" color="light.50"> Pais : </text>
        <input
          w="50%"
          h="50px"
          v-model="pais"
          @blur="Country"
          @focus="enable"
          bg="light.50"
        />
        <text font-size="15px" mr="35%" color="light.50">Ciudad : </text>
        <input
          w="50%"
          h="50px"
          v-model="dpto"
         
          @blur="Time"
          bg="light.50"

        />
        <text
          v-if="clima != 'error' && country != null && clima != null"
          font-size="50px"
          color="light.50"
          >{{ Math.round(clima) }}°C</text
        >

        <text
          v-if="clima == 'error' || country == 'error'"
          font-size="17px"
          color="red.700"
        >
          {{ TextError }}</text
        >

        <box v-if="clima != 'error'">
          <center>
            <image
              class="icon"
              v-for="icon in Description"
              :key="icon"
              :source="{
                uri: 'https://openweathermap.org/img/wn/' + icon.icon + '.png',
              }"
            />
          </center>
          <text
            font-size="50px"
            color="light.50"
            v-for="dat in Description"
            :key="dat"
            >{{ dat.description }}</text
          >
        </box>
      </center>
    </view>
  </native-base-provider>
</template>
<style>
.icon {
  width: 250px;
  height: 200px;
}
</style>
<script>
import {
  NativeBaseProvider,
  View,
  Input,
  Text,
  Center,
  Box,
} from "native-base";
import axios from "axios";

export default {
  components: {
    NativeBaseProvider,
    View,
    Input,
    Text,
    Center,
    Box,
  },
  data: function () {
    return {
      clima: null,
      dpto: "",
      pais: "",
      country: null,
      iSO: "",
      Description: null,
      TextError: "",
    };
  },
  methods: {
    Time: function () {
      if (this.pais != "" && this.dpto != "") {
        axios
          .get(
            "https://api.openweathermap.org/data/2.5/weather?q=" +
              this.dpto +
              "," +
              this.iSO +
              "&appid=e947ad0ec7d762e6bbbbc269557d8de8&units=metric&lang=sp"
          )
          .then((response) => (this.clima = response.data.main.temp))
          .then((data) => {})
          .catch((error) => {
            this.clima = "error";
            this.TextError = "la ciudad no existe en el pais ingresado";
          });

        axios
          .get(
            "https://api.openweathermap.org/data/2.5/weather?q=" +
              this.dpto +
              "," +
              this.iSO +
              "&appid=e947ad0ec7d762e6bbbbc269557d8de8&units=metric&lang=sp"
          )
          .then((response) => (this.Description = response.data.weather))
          .then((data) => {})
          .catch((error) => {
            

          });
          console.log(this.pais);
           console.log(this.dpto);
           console.log(this.iSO);
      }
    },

  
    Country: function () {
      if (this.pais != "") {
        let pais = this.pais.toLowerCase();
        if (pais == "estados unidos de america") {
          pais = "United States of America";
        }
        axios
          .get(
            "https://restcountries.com/v3.1/name/" + pais + "?fullText=false"
          )
          .then((response) => (this.country = response.data))
          .then((data) => {
            data.forEach((a) => {
              if (pais != a.name.common.toLowerCase()) { 
            this.clima = "error";
                this.dpto = "";
                this.country = null;
                this.pais = "";
                this.iSO = "";
                this.Description = null;
            this.TextError = "el pais ingresado no existe";
              }else{
                  this.iSO = a.cca2;
                }
            });
          })
          .catch((error) => {
            this.clima = "error";
                this.dpto = "";
                this.country = null;
                this.pais = "";
                this.iSO = "";
                this.Description = null;
            this.TextError = "el pais ingresado no existe";
          });
      }else{
        this.TextError = "no has ingresado un pais";
                this.clima = "error";
                this.dpto = "";
                this.country = null;
                this.pais = "";
                this.iSO = "";
                this.Description = null;
        }
    },
    enable: function () {
      this.dpto = "";
      this.country = null;
      this.clima = null;
      this.pais = "";
      this.iSO = "";
      this.Description = null;
    },
  },
};
</script>
