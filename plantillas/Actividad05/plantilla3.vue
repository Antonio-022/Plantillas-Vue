<template>
  <native-base-provider>
    <box w="100%" h="100%">
 
      <box class="box1" h= "100px"> </box>
      <box class="box2" h= "200px"> </box>
      <box class="box3" h= "50px"> </box>
      <box class="box4" h= "100%"> </box>
    </box>
  </native-base-provider>
</template>
<style>
</style>
<script>
import {
  NativeBaseProvider,
  Text,
  Box,
  Flex,
  Spacer,
  Center,
  Button,
} from "native-base";
export default {
  
  components: {

    Text,
    NativeBaseProvider,
    Box,
    Flex,
    Spacer,
    Center,
    Button,

  },
  data: function () {
    return {};
  },
  methods: {

  },
};
</script>
<style>
.box1 {
  
  background-color: #3aba1c;
}
.box2 {
  background-color: #2299a1;
}
.box3 {

  background-color: #4198cc;
}
.box4 {

  background-color: #32abcb;
}
</style>

