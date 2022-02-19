<template>
  <native-base-provider>
    <view class="container" bg="dark.50" w="100%" h="100%">
      <center>
        <container mb="5">
          <text top="20%" fontSize="22" color="emerald.500" mt="9" class="title">
            EJERCICIO 04
          </text>
        </container>
      </center>
      <form-control px="3">
        <input fontSize="20" color="light.50" mt="5" width="100%" height="15%" variant="rounded" placeholder="Escribe" mb="7"/>
        <view px="4" top="10%">
          <container flexDirection="row" mg="2" mb="4">
            <button size="sm" ml="7">
              <text fontSize="50"> 1 </text>
            </button>
            <button size="sm" colorScheme="secondary" ml="7">
              <text fontSize="50"> 2 </text>
            </button>
            <button size="sm" ml="7">
              <text fontSize="50"> 3 </text>
            </button>
          </container>
          <container flexDirection="row" mg="2" mb="4">
            <button size="sm" ml="7">
              <text fontSize="50"> 4 </text>
            </button>
            <button size="sm" colorScheme="secondary" ml="7">
              <text fontSize="50"> 5 </text>
            </button>
            <button size="sm" ml="7">
              <text fontSize="50"> 6 </text>
            </button>
          </container>
          <container flexDirection="row" mg="2" mb="4">
            <button size="sm" ml="7">
              <text fontSize="50"> 7 </text>
            </button>
            <button size="sm" colorScheme="secondary" ml="7">
              <text fontSize="50"> 8 </text>
            </button>
            <button size="sm" ml="7">
              <text fontSize="50"> 9 </text>
            </button>
          </container>
        </view>
        <view top="10%" px="5">
          <button>Calcular Transpuesta</button>
        </view>
      </form-control>
      <center>
      <stack direction="row" px="3" mt="12">

        <view class="check" mr="30%">
          <checkbox mb="10"></checkbox>
          <checkbox></checkbox>
        </view>
        <view class="radio">
         <view  mb="3" >
          <radio-button class="first" uncheckedColor="white" value="first" >
          </view>
          <view  >
          <radio-button value="second" status="checked" >
          </view>
        </view>
      </stack>
      </center>
    </view>
  </native-base-provider>
</template>
<script>
import {
  NativeBaseProvider,
  Center,
  Container,
  Heading,
  Text,
  Input,
  FormControl,
  Button,
  Checkbox,
  View,
  Stack,
} from "native-base";
import { RadioButton } from "react-native-paper";
export default {
  components: {
    NativeBaseProvider,
    Center,
    RadioButton,
    Container,
    Heading,
    Text,
    Input,
    FormControl,
    Button,
    Checkbox,
    View,
    Stack,
  },
  data() {
    return {};
  },
  methods: {
    exclaim() {},
  },
};
</script>
<style>
.radio {
  background-color: rgb(17, 50, 121);
  display: flex;
}
</style>