<template>
  <native-base-provider>
    <status-bar background-color="#0369a1" bar-style="light-content" />
    <view bg="info.500" w="100%" h="100%">
      <keyboard-avoiding-view>
        <view class="header" w="100%" bg="info.700">
          <center>
            <text ml="2" mt="3" font-size="20px" color="light.50"
              >{{ name }}
            </text>
          </center>
          <view flex-direction="row">
            <view flex-direction="row">
              <text ml="2" mt="3" color="light.50">Matriz A : </text>
              <input
                keyboardType="numeric"
                v-model="m"
                mt="2"
                class="dimensiones"
                placeholder="m"
                bg="light.50"
                width="30px"
                height="35px"
              />
              <text mt="3" color="light.50"> x</text>
              <input
                keyboardType="numeric"
                v-model="n"
                mt="2"
                class="dimensiones"
                placeholder="n"
                bg="light.50"
                ml="2"
                width="30px"
                height="35px"
              />
            </view>
            <view flex-direction="row">
              <text mt="3" ml="2" color="light.50">Matriz B : </text>
              <input
                keyboardType="numeric"
                v-model="x"
                mt="2"
                class="dimensiones"
                placeholder="n"
                bg="light.50"
                width="30px"
                height="35px"
              />
              <text mt="3" color="light.50"> x</text>
              <input
                keyboardType="numeric"
                v-model="p"
                mt="2"
                class="dimensiones"
                placeholder="p"
                bg="light.50"
                ml="2"
                mr="2"
                width="30px"
                height="35px"
              />
            </view>
            <button
              mt="2"
              mb="2"
              size="sm"
              w="70px"
              height="35px"
              bg="success.500"
              :on-press="mostrar"
            >
              Crear
            </button>
          </view>
        </view>
        <view w="100%">
          <view w="100px">
            <button bg="danger.500" :on-press="del">Limpiar</button>
          </view>
        </view>
      </keyboard-avoiding-view>
      <scroll-view>
        <center>
          <scroll-view maxW="350" h="670" mt="5">
            <scroll-view horizontal>
              <view flex-direction="column">
                <text
                  v-if="clave == 1"
                  color="light.50"
                  class="dimensiones"
                  mt="3"
                  >Matriz A</text
                >
                <view v-if="clave == 1" flex-direction="column">
                  <box
                    v-for="filas in Matriz_A"
                    v-bind:key="filas.c"
                    flex-direction="row"
                    px="2"
                  >
                    <box
                      v-for="columnas in filas"
                      v-bind:key="columnas.i"
                      mb="2"
                      px="1"
                    >
                      <input
                        v-if="claveM == 2"
                        keyboardType="numeric"
                        width="50px"
                        height="50px"
                        bg="light.50"
                        color="dark.50"
                        class="input_matriz"
                        v-model="columnas.valor"
                      />
                    </box>
                  </box>
                </view>
                <text
                  v-if="clave == 1"
                  class="dimensiones"
                  color="light.50"
                  mt="3"
                  >Matriz B</text
                >
                <view v-if="clave == 1" flex-direction="column">
                  <box
                    v-for="filas in Matriz_B"
                    v-bind:key="filas.c"
                    flex-direction="row"
                    px="2"
                  >
                    <box
                      v-for="columnas in filas"
                      v-bind:key="columnas.i"
                      mb="2"
                      px="1"
                    >
                      <input
                        v-if="claveM == 2"
                        keyboardType="numeric"
                        width="50px"
                        height="50px"
                        bg="light.50"
                        color="dark.50"
                        class="input_matriz"
                        v-model="columnas.valor"
                      />
                    </box>
                  </box>
                </view>
                <text
                  v-if="Mclave == 2"
                  class="dimensiones"
                  color="light.50"
                  mt="3"
                  >resultado</text
                >
                <view flex-direction="column">
                  <box
                    v-for="filas in resultadoM"
                    v-bind:key="filas.c"
                    flex-direction="row"
                    px="2"
                  >
                    <box
                      v-for="columnas in filas"
                      v-bind:key="columnas.i"
                      mb="2"
                      px="1"
                    >
                      <input
                        v-if="claveC == 3"
                        keyboardType="numeric"
                        width="50px"
                        height="50px"
                        bg="light.50"
                        color="dark.50"
                        class="input_matriz"
                        v-model="columnas.valor"
                      />
                    </box>
                  </box>
                </view>
              </view>
            </scroll-view>
          </scroll-view>
        </center>
      </scroll-view>
      <keyboard-avoiding-view class="footer_container">
        <view class="footer">
          <button
            v-if="name == 'Suma'"
            size="lg"
            bg="orange.700"
            :on-press="sumar"
          >
            Calcular
          </button>
          <button
            v-if="name == 'Resta'"
            size="lg"
            bg="warning.600"
            :on-press="resta"
          >
            Calcular
          </button>
          <button
            v-if="name == 'Producto'"
            size="lg"
            bg="warning.600"
            :on-press="Producto"
          >
            Calcular
          </button>
        </view>
      </keyboard-avoiding-view>
    </view>
  </native-base-provider>
</template>
<style>
.input_matriz {
  text-align: center;
}
.footer_container {
  position: absolute;
  bottom: 0;
  width: 100%;
}
.dimensiones {
  text-align: center;
}
.header {
  display: flex;
}
</style>
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
  Container,
  ScrollView,
} from "native-base";
import { KeyboardAvoidingView } from "react-native";
export default {
  props: {
    navigation: {
      type: Object,
    },
  },
  components: {
    NativeBaseProvider,
    Container,
    KeyboardAvoidingView,
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
      name: "",
      m: "",
      n: "",
      x: "",
      p: "",
      PM: "",
      flame: false,
      filasA: 0,
      columnaA: 0,
      filasB: 0,
      columnaB: 0,
      Matriz_A: [],
      Matriz_B: [],
      resultadoM: [],
      clave: 0,
      claveC: 0,
      Mclave: 0,
      claveM: 0,
    };
  },
  methods: {
    mostrar: function () {
      if (CasillasVacias(this.m, this.n, this.x, this.p)) {
        if (Entero(this.m, this.n, this.x, this.p)) {
          this.claveM = 2;
          this.flame = true;
          this.Matriz_A = [];
          this.Matriz_B = [];
          this.resultadoM = [];
          this.Mclave = 0;
          var auxiliarA = [];
          var contA = 1;
          this.clave = 1;
          this.claveC = 2;
          this.filasA = Number(this.m);
          this.columnaA = Number(this.n);
          for (var i = 0; i < this.filasA; i++) {
            for (var j = 0; j < this.columnaA; j++) {
              auxiliarA.push({ id: contA, valor: 2 });
              contA++;
            }
            this.Matriz_A.push(auxiliarA);
            auxiliarA = [];
          }
          var auxiliarB = [];
          var contB = 1;
          this.filasB = Number(this.x);
          this.columnaB = Number(this.p);
          for (var i = 0; i < this.filasB; i++) {
            for (var j = 0; j < this.columnaB; j++) {
              auxiliarB.push({ id: contB, valor: 1 });
              contB++;
            }
            this.Matriz_B.push(auxiliarB);
            auxiliarB = [];
          }
        } else {
          alert("no se aceptan caracteres o letras");
        }
      } else {
        alert("hay casillas vacias en las dimensiones");
      }
    },
    sumar: function () {
      if (this.flame == true) {
        this.claveC = 3;
        this.clave = 1;
        this.Mclave = 2;
        this.claveM = 2;
        this.resultadoM = [];
        var contB = 1;
        var auxiliarB = [];

        this.filasB = Number(this.x);
        this.columnaB = Number(this.p);
        for (var i = 0; i < this.filasB; i++) {
          for (var j = 0; j < this.columnaB; j++) {
            auxiliarB.push({
              id: contB,
              valor:
                "" +
                (Number(this.Matriz_A[i][j].valor) +
                  Number(this.Matriz_B[i][j].valor)),
            });
            contB++;
          }
          this.resultadoM.push(auxiliarB);
          auxiliarB = [];
        }
      } else {
        alert("crea las matrices primero");
      }
    },
    resta: function () {
      if (this.flame == true) {
        this.claveC = 3;
        this.clave = 1;
        this.Mclave = 2;
        this.claveM = 2;
        this.resultadoM = [];
        var contB = 1;
        var auxiliarB = [];

        this.filasB = Number(this.x);
        this.columnaB = Number(this.p);
        for (var i = 0; i < this.filasB; i++) {
          for (var j = 0; j < this.columnaB; j++) {
            auxiliarB.push({
              id: contB,
              valor:
                "" +
                (Number(this.Matriz_A[i][j].valor) -
                  Number(this.Matriz_B[i][j].valor)),
            });
            contB++;
          }
          this.resultadoM.push(auxiliarB);
          auxiliarB = [];
        }
      } else {
        alert("crea las matrices primero");
      }
    },
    Producto: function () {
      if (this.flame == true) {
        this.claveC = 3;
        this.clave = 1;
        this.claveM = 2;
        this.Mclave = 2;
        this.resultadoM = [];
        var contB = 0;
        var auxiliarB = [];
        this.filasA = Number(this.m);
        this.columnaA = Number(this.n);
        this.filasB = Number(this.x);
        this.columnaB = Number(this.p);
        for (var i = 0; i < this.filasA; i++) {
          for (var j = 0; j < this.columnaB; j++) {
            var rrr = [];
            for (let y = 0; y < this.filasB; y++) {
              rrr.push(
                parseInt(this.Matriz_A[i][y].valor) *
                  parseInt(this.Matriz_B[y][j].valor)
              );
            }
            var resultado = 0;
            for (let x = 0; x < rrr.length; x++) {
              resultado += rrr[x];
            }
            auxiliarB.push({ id: contB, valor: "" + resultado });
            contB++;
          }
          this.resultadoM.push(auxiliarB);
          auxiliarB = [];
        }
      } else {
        alert("crea las matrices primero");
      }
    },
    del: function () {
      this.clave = 0;
      this.Mclave = 0;
      this.claveC = 0;
      this.m = "";
      this.n = "";
      this.x = "";
      this.p = "";
    },
  },

  beforeMount() {
    let nombre = this.navigation.getParam("name");
    this.name = nombre;
  },
};

function Entero(valor1, valor2, valor3, valor4) {
  if (
    !isNaN(parseFloat(valor1)) &&
    !isNaN(parseFloat(valor2)) &&
    !isNaN(parseFloat(valor3)) &&
    !isNaN(parseFloat(valor4))
  ) {
    return true;
  }
  return false;
}
function CasillasVacias(valor1, valor2, valor3, valor4) {
  if ((valor1, valor2, valor3, valor4 != "")) {
    return true;
  }
  return false;
}
</script>