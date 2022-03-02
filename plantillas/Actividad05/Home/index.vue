<template>
  <native-base-provider>
    <status-bar background-color="#0369a1" bar-style="light-content" />
    <view  class="container" bg="info.700" h="100%" w="100%">
      
      <center>
        <view >
            <text color="light.50" font-size="50px" >MATRICES</text>
          <view>
            <button mb="5" h="50px" size="lg" :on-press="suma" mt="10">Suma</button>
            <button mb="5" h="50px" size="lg" :on-press="resta" >Resta</button>
            <button mb="5" h="50px" size="lg" :on-press="transpuesta" >Transpuesta</button>
            <button mb="5" h="50px" size="lg" :on-press="producto" >Producto</button>
            <button mb="5" h="50px" size="lg" :on-press="potencia" >Potencia</button>
          </view>
            
        </view>
      </center>
 
</view>
  </native-base-provider>
</template>
<style>
.container
{
  justify-content: center;
}
</style>
<script>

import {
  NativeBaseProvider,
  Box,
  Button,
  View,
  Text,
  Center,
} from "native-base";

export default {
  props: {
    navigation: {
      type: Object,
    },
  },
  components: {
    NativeBaseProvider,
    Box,
    Button,
    View,
    Text,
    Center,
    
  },
  data: function () {
    return {
        datas:"",
    };
  },
  methods: {
    suma: function () {
    this.navigation.navigate("Calculator",{name: 'Suma'});
    },
        resta: function () {
    this.navigation.navigate("Calculator",{name: 'Resta'});
        },
        transpuesta: function () {
    this.navigation.navigate("App2_T",{name: 'Transpuesta'});
    },
        producto: function () {
    this.navigation.navigate("Calculator",{name: 'Producto'});
    },
        potencia: function () {
     this.navigation.navigate("App2_T",{name: 'Potencia'});
    },
  },
};
</script>