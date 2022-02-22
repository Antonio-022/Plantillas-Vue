<template>
  <native-base-provider>
    <view bg="success.300" w="100%" h="100%">
      <center>
        <view flex-direction="row" mt="10%">
          <text mt="10px"> filas : </text>
          <view>
            <input
              width="50px"
              height="50px"
              v-model="m"
              bg="light.100"
              color="dark.50"
              keyboardType="numeric"
            />
          </view>
          <text ml="10px" mt="10px"> columnas : </text>
          <view>
            <input
              width="50px"
              height="50px"
              v-model="n"
              bg="light.100"
              color="dark.50"
              keyboardType="numeric"
            />
          </view>
        </view>
      </center>
      <center>
        <button
          size="sm"
          w="85px"
          height="40px"
          mb="5"
          mt="5"
          :on-press="mostrar"
        >
          mostrar
        </button>
      </center>
      <center>
        <scroll-view maxW="350" h="600">
          <scroll-view horizontal>
            <view flex-direction="row">
              <box v-for="i in columna" :key="i" px="1">
                <box v-for="j in filas" :key="j" mb="2">
                  <input
                    keyboardType="numeric"
                    width="50px"
                    height="50px"
                    bg="light.100"
                    color="dark.50"
                    
                  />
                </box>
              </box>
            </view>
          </scroll-view>
        </scroll-view>
      </center>
    </view>
  </native-base-provider>
</template>
<script>
import {
  NativeBaseProvider,
  Input,
  Box,
  Heading,
  Spacer,
  View,
  Center,
  Button,
  Text,
  ScrollView,
} from "native-base";
export default {
  components: {
    NativeBaseProvider,
    Input,
    Box,
    Heading,
    View,
    Spacer,
    Center,
    Button,
    Text,
    ScrollView,
  },
  data() {
    return {
      m: "",
      n: "",
      filas: 0,
      columna: 0,
      tabla: [[2,2],[1,1]],
    };
  },
  methods: {
    mostrar: function () {
      this.filas = Number(this.m);
      this.columna = Number(this.n);
    },
  },
};
</script>

