<template>
  <native-base-provider>
    <box w="100%" h="100%">
 
      <box class="box1"> </box>
      <box class="box2"> </box>
      <box class="box3"> </box>
      <box class="box4"> </box>
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
  height: 100px;
  background-color: #3aba1c;
}
.box2 {
  height: 200px;
  background-color: #2299a1;
}
.box3 {
  height: 50px;
  background-color: #4198cc;
}
.box4 {
  height: 100%;
  background-color: #32abcb;
}
</style>

