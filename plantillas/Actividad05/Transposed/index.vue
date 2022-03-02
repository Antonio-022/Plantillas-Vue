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
          <center>
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
              <button
                mt="2"
                mb="2"
                size="sm"
                w="70px"
                ml="5%"
                height="35px"
                bg="success.500"
                :on-press="mostrar"
              >
                Crear
              </button>
            </view>
          </center>
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
                <view flex-direction="row" v-if="name == 'Potencia'">
                  <center>
                    <text v-if="clave == 1" color="light.50"> Potencia : </text>
                  </center>
                  <input
                    keyboardType="numeric"
                    v-if="clave == 1"
                    v-model="PM"
                    bg="light.50"
                    color="dark.50"
                    w="50px"
                    h="50px"
                  />
                </view>
                <text
                  v-if="clave == 1"
                  color="light.50"
                  class="dimensiones"
                  mt="3"
                  >Matriz A</text
                >
                <view flex-direction="column">
                  <box
                    v-for="filasa in Matriz_A"
                    :key="filasa.a"
                    flex-direction="row"
                    px="2"
                  >
                    <box
                      v-for="columnasa in filasa"
                      :key="columnasa.b"
                      mb="2"
                      px="1"
                    >
                      <input
                        v-if="clave == 1"
                        keyboardType="numeric"
                        width="50px"
                        height="50px"
                        bg="light.50"
                        color="dark.50"
                        class="input_matriz"
                        v-model="columnasa.valor"
                      />
                    </box>
                  </box>
                </view>

                <text
                  v-if="Mclave == 1"
                  class="dimensiones"
                  color="light.50"
                  mt="3"
                  >resultado</text
                >
                <view flex-direction="column">
                  <box
                    v-for="filasb in resultadoM"
                    :key="filasb.c"
                    flex-direction="row"
                    px="2"
                  >
                    <box
                      v-for="columnasb in filasb"
                      :key="columnasb.d"
                      mb="2"
                      px="1"
                    >
                      <input
                        v-if="Mclave == 1"
                        keyboardType="numeric"
                        width="50px"
                        height="50px"
                        bg="light.50"
                        color="dark.50"
                        class="input_matriz"
                        v-model="columnasb.valor"
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
            v-if="name == 'Transpuesta'"
            size="lg"
            bg="warning.600"
            :on-press="Transpuesta"
          >
            Calcular
          </button>
          <button
            v-if="name == 'Potencia'"
            size="lg"
            bg="warning.600"
            :on-press="Potencia"
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
      idF: "",
      idC: "",
      PM: "",
      filasA: 0,
      columnaA: 0,
      Matriz_A: [],
      resultadoM: [],
      clave: 0,
      claveC: 0,
      claveM: 0,
      Mclave: 0,
      flame: false,
    };
  },
  methods: {
    del: function () {
      this.clave = 0;
      this.Mclave = 0;
      this.claveC = 0;
      this.m = "";
      this.n = "";
    },
    mostrar: function () {
      if (CasillasVacias(this.m, this.n, this.x, this.p)) {
        if (Entero(this.m, this.n, this.x, this.p)) {
          this.flame = true;
          this.Matriz_A = [];
          this.resultadoM = [];
          this.Mclave = 0;
          var auxiliarA = [];
          var contA = 1;
          this.clave = 1;
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
        } else {
          alert("no se aceptan caracteres o letras");
        }
      } else {
        alert("hay casillas vacias en las dimensiones");
      }
    },

    Transpuesta: function () {
      if (this.flame == true) {
        this.clave = 1;
        this.Mclave = 1;
        this.resultadoM = [];
        var contB = 1;
        var auxiliarB = [];
        for (var i = 0; i < this.filasA; i++) {
          for (var j = 0; j < this.columnaA; j++) {
            auxiliarB.push({
              id: contB,
              valor: "" + Number(this.Matriz_A[j][i].valor),
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
    Potencia: function () {
      if (this.flame == true) {
        this.resultadoM = [];
        this.clave = 1;
        this.Mclave = 1;
        let potencia = this.PM;
        let dimension = this.filasA;
        let matrizR = [];
        let matriz = [];
        let auxiliar = [];
        let contP = 1;
        let auxiliar2 = [];
        for (var i = 0; i < this.filasA; i++) {
          for (var j = 0; j < this.columnaA; j++) {
            auxiliar.push(this.Matriz_A[i][j].valor);
          }
          matriz.push(auxiliar);
          auxiliar = [];
        }
        MatrizConstante = matriz;
        matrizR = PotenciaDatos(matriz, potencia, dimension);
        if (matrizR != null) {
          for (let i = 0; i < dimension; i++) {
            for (let j = 0; j < dimension; j++) {
              auxiliar2.push({ id: contP, valor: "" + matrizR[i][j] });
              contP++;
            }
            this.resultadoM.push(auxiliar2);
            auxiliar2 = [];
          }
        } else {
          alert("estas tratando de realizar una matriz inversa");
          this.Mclave = 0;
        }
      } else {
        alert("crea las matrices primero");
      }
    },
  },
  beforeMount() {
    let nombre = this.navigation.getParam("name");
    this.name = nombre;
  },
};
let MatrizConstante = [];
function PotenciaDatos(Matriz, p, filas) {
  let matrizR = [];
  let auxiliarB = [];

  let R = 1;
  if (p > 0) {
    if (R < p) {
      for (let i = 0; i < filas; i++) {
        for (let j = 0; j < filas; j++) {
          var rrr = [];
          for (let k = 0; k < filas; k++) {
            rrr.push(parseInt(Matriz[i][k]) * parseInt(MatrizConstante[k][j]));
          }
          var resultado = 0;
          for (let x = 0; x < rrr.length; x++) {
            resultado += rrr[x];
          }
          auxiliarB.push(resultado);
        }
        matrizR.push(auxiliarB);
        auxiliarB = [];
      }
      return PotenciaDatos(matrizR, p - 1, filas);
    }
    return Matriz;
  } else if (p == 0) {
    for (let i = 0; i < filas; i++) {
      for (let j = 0; j < filas; j++) {
        if (i == j) {
          auxiliarB.push(1);
        } else {
          auxiliarB.push(0);
        }
      }
      matrizR.push(auxiliarB);
      auxiliarB = [];
    }
    return matrizR;
  } else {
    return null;
  }
}
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