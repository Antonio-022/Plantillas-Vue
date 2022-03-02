<template>
  <native-base-provider>
    <box w="100%" h="100%" bg="indigo.300">
      <center>
        <heading class="title" color="light.50" top="25%">
          Gato Siames
        </heading>
        <view top="35%">
          <image :source="require('./gato.jpg')" class="img" />
        </view>
      </center>
      <view top="15%">
        <text pt="3" color="light.50" class="details-content"> Detalle : </text>
        <center>
          <text class="details" pt="3" color="light.50" >Es un gato alargado y elegante. Tiene cuerpo, cuello, patas y cola
            alargados. Esta raza es de tamaño medio, aunque con músculos
            proporcionados. El siamés es un gato de extremos. Su cabeza es un
            triángulo alargado. Las orejas altas están situadas sobre la cabeza
            a continuación de dicho triángulo. Su nariz es larga y recta y las
            patas son largas y esbeltas. Tiene la cola larga y rematada en
            punta. Los ojos, almendrados, son de un verde brillante.
          </text>
        </center>
      </view>
    </box>
  </native-base-provider>
</template>
<script>
import {
  NativeBaseProvider,
  Text,
  Box,
  Flex,
  Spacer,
  Center,
  View,
  Button,
  Heading,
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
    View,
    Heading,
  },
};
</script>
<style>
.title {
  font-size: 30px;
}
.img {
  width: 200px;
  height: 200px;
  border-radius: 100px;
}
.details-content{
  font-size: 25px;
}
.details{
    font-size: 25px;
    color: black;
    padding: 10px;
}
</style>