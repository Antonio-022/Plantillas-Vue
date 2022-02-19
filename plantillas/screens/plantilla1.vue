<template>
  <native-base-provider>
    <box class="container">
      <center class="img-content">
        <image :source="require('./vue.jpg')" class="img" />
        <view mt="15">
          <stack direction="row" px="3" mb="2.5" mt="15" >
            <button :onPress="plantilla1" size="sm" w="185px" class="btn1">plantilla 1</button>
            <button :onPress="plantilla2 " variant="subtle" class="btn2" w="185px" h="50px" size="sm">plantilla 2</button>
          </stack>
          <stack px="3" mb="2.5" mt="15">
            <button h="50px" :onPress="plantilla3"  class="btn3">plantilla 3</button>
          </stack>
          <stack direction="row" px="3"  mt="15" >
            <button :onPress="plantilla4" size="sm"  class="btn4" w="85px">Plantilla 4</button>
            <button variant="subtle" class="btn5" w="85px" h="55px" size="sm">coming soon </button>
            <button size="sm"  class="btn6" w="85px">coming soon</button>
            <button variant="subtle" class="btn7"  h="55px" w="85px" size="sm">coming soon</button>
          </stack>
        </view>
      </center>
    </box>
  </native-base-provider>
</template>

<style>
.container {
  width: 100%;
  height: 100%;
  background-color: cadetblue;
}
.img {
  width: 95%;
  height: 500px;
}
.img-content {
  top: 5%;
}
.btn1
{
  margin-right: 5%;
}

.btn4 , .btn5 , .btn6
{
  margin-right: 4%;
}
</style>

<script>

import {
  NativeBaseProvider,
  Box,
  Button,
  Center,
  View,
  Stack,
  Flex,
  Spacer,
} from "native-base";

export default {
    props: {
    navigation: {
      type: Object
    }
  },
  components: {
    NativeBaseProvider,
    Box,
    Center,
    Button,
    View,
    Stack,
    Flex,
    Spacer,
  },
  data: function () {
    return {
 
    };
  },
  methods: {
    plantilla1: function () {
       this.navigation.navigate("option1");
    },
        plantilla2: function () {
       this.navigation.navigate("option2");
    },
        plantilla3: function () {
       this.navigation.navigate("option3");
    },
        plantilla4: function () {
       this.navigation.navigate("option4");
    },
      
  },
};
</script>