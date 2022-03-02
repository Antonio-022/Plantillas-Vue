<template>
  <native-base-provider>
    <box class="container" bg="warning.300" h="100%" w="100%">
      <center>
        <view mt="20%">
            <text color="light.50" font-size="40px" >MATRICES</text>
          <view>
            <button mb="5" h="50px" size="lg" :on-press="suma" mt="10">Suma</button>
            <button mb="5" h="50px" size="lg" >Resta</button>
            <button mb="5" h="50px" size="lg" >Transpuesta</button>
            <button mb="5" h="50px" size="lg" >Producto</button>
            <button mb="5" h="50px" size="lg" >Potencia</button>
          </view>
             <text color="light.50" font-size="40px">APIS RES</text>
          <view>
            <button mb="5" h="50px" size="lg" mt="10">Google Maps</button>
            <button mb="5" h="50px" size="lg" >Clima</button>
          </view>
        </view>
      </center>
      <plantilla-m :M=TipoA>
    </box>
     
  </native-base-provider>
</template>

<script>
import PlantillaM from './plantilla5.vue';
import {
  NativeBaseProvider,
  Box,
  Button,
  Center,
  View,
  Stack,
  Flex,
  Text,
  Spacer,
} from "native-base";

export default {
  props: {
    navigation: {
      type: Object,
    },
  },
  components: {
    PlantillaM,
    NativeBaseProvider,
    Box,
    Center,
    Button,
    View,
    Stack,
    Flex,
    Text,
    Spacer,
  },
  data: function () {
    return {
        TipoA:0,
    };
  },
  methods: {
    suma: function () {
      this.TipoA = 1;
      this.navigation.navigate("option5");   
    },

  },
};
</script>