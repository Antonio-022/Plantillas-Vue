<template>
  <native-base-provider>
    <view class="container" bg="orange.300" w="100%" h="100%">
      <center>
        <container mb="5">
          <text color="light.50" mt="10" fontSize="30">
            EJERCICIO 04
          </text>
        </container>
      </center>
      <form-control>
        <input
          width="100%"
          height="10%"
          variant="rounded"
          placeholder="Escribe"
          mb="3"
          color="dark.50"
          bg="light.50"
          fontSize="20"
        />
        <center>
          <view px="2" ml="5%" mt="10%">
          <container flexDirection="row" mg="2" mb="3%">
            <button size="sm" width="24%">
              <text fontSize="50">
                {{ matris[0][0] }}
              </text>
            </button>
            <button size="sm" colorScheme="secondary" ml="7" width="24%">
              <text fontSize="50">
                {{ matris[0][1] }}
              </text>
            </button>
            <button size="sm" ml="7" width="24%">
              <text fontSize="50">
                {{ matris[0][2] }}
              </text>
            </button>
          </container>
          <container flexDirection="row" mg="2" mb="3%">
            <button size="sm" width="24%">
              <text fontSize="50">
                {{ matris[1][0] }}
              </text>
            </button>
            <button size="sm" colorScheme="secondary" ml="7" width="24%">
              <text fontSize="50">
                {{ matris[1][1] }}
              </text>
            </button>
            <button size="sm" ml="7" width="24%">
              <text fontSize="50">
                {{ matris[1][2] }}
              </text>
            </button>
          </container>
          <container flexDirection="row" mg="2" mb="3%">
            <button size="sm" width="24%">
              <text fontSize="50">
                {{ matris[2][0] }}
              </text>
            </button>
            <button size="sm" colorScheme="secondary" ml="7" width="24%">
              <text fontSize="50">
                {{ matris[2][1] }}
              </text>
            </button>
            <button size="sm" ml="7" width="24%">
              <text fontSize="50">
                {{ matris[2][2] }}
              </text>
            </button>
           
          </container>
           </view>
          <button
            size="sm"
            ml="7"
            width="70%"
            height="10%"
            mr="6%"
            mb="2"
            :on-press="calularTranpuesta"
          >
            Calcular Transpuesta
          </button>
          <stack direction="row">
            <container mr="25%">
              <view mb="3">
                <checkbox status="checked" />
              </view>
              <view>
                <checkbox uncheckedColor="white" />
              </view>
            </container>
            <container>
              <view mb="3">
                <radio-button class="first" uncheckedColor="white" />
              </view>
              <view>
                <radio-button status="checked" />
              </view>
            </container>
          </stack>
        </center>
      </form-control>
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
  View,
  Stack,
} from "native-base";

import { Checkbox, RadioButton } from "react-native-paper";

export default {
  components: {
    View,
    NativeBaseProvider,
    Center,
    Container,
    Heading,
    Text,
    Input,
    FormControl,
    Button,
    Checkbox,
    Stack,
    RadioButton,
  },
  data() {
    return {
      matris: [
        [1, 2, 3],
        [4, 5, 6],
        [7, 8, 9],
      ],
    };
  },
  methods: {
    exclaim() {},
    calularTranpuesta: function () {
      this.matris = [
        [1, 4, 7],
        [2, 5, 8],
        [3, 6, 9],
      ];

      /*   for (let f = 0; f < 3; f++) {
  
          for (let c = 0; c < 3; c++) {
            
            this.matris[f][c] = this.matris[c][f];

          }
          
        }
        alert(this.matris);*/
    },
  },
};
</script>
<style>

</style>
