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
            <button h="50px" :onPress="plantilla5"  class="btn3"   size="sm">calculadora de matrices </button>
           
          </stack>
          <stack direction="row" px="3"  mt="15" >
            <button  :onPress="plantilla3" variant="subtle" w="85px" size="sm"  class="btn4">Plantilla 3</button>
            <button :onPress="plantilla4" size="sm"  class="btn5" w="85px">Plantilla 4</button>
            <button size="sm" variant="subtle"  class="btn6" w="85px">coming soon</button>
            <button  class="btn7"  w="85px" size="sm">coming soon</button>
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
            plantilla5: function () {
       this.navigation.navigate("option5");
    },
      
  },
};
</script>