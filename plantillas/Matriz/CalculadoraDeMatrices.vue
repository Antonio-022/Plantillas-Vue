<template>
  <native-base-provider>
    <status-bar background-color="#0891b2" bar-style="light-content" />
    <view bg="warning.300" w="100%" h="100%">
      <keyboard-avoiding-view>
        <view class="header" w="100%" bg="primary.600" flex-direction="row">
          <text  ml="2" mt="3" color="light.50">Matriz A : </text>
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
      </keyboard-avoiding-view>

      <scroll-view>

        <center>

            <scroll-view maxW="350" h="670" mt="5">
              <scroll-view horizontal>
                <view>
                <text v-if="clave == 1" color="light.50" class="dimensiones"  mt="3">Matriz A</text>
                <view flex-direction="column">
                  <box
                    v-for="filas in Matriz_A"
                    :key="filas.idF"
                    flex-direction="row"
                    px="2"
                  >
                    <box
                      v-for="columnas in filas"
                      :key="columnas.idC"
                      mb="2"
                      px="1"
                    >
                      <input
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
 
                <text v-if="clave == 1" class="dimensiones"  color="light.50"  mt="3">Matriz B</text>
                <view flex-direction="column">
                  <box
                    v-for="filas in Matriz_B"
                    :key="filas.idF"
                    flex-direction="row"
                    px="2"
                  >
                    <box
                      v-for="columnas in filas"
                      :key="columnas.idC"
                      mb="2"
                      px="1"
                    >
                      <input
                        
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

                 
                <text v-if="Mclave == 2" class="dimensiones"  color="light.50"  mt="3">resultado</text>
                <view flex-direction="column">
                  <box
                    v-for="filas in resultadoM"
                    :key="filas.idF"
                    flex-direction="row"
                    px="2"
                  >
                    <box
                      v-for="columnas in filas"
                      :key="columnas.idC"
                      mb="2"
                      px="1"
                    >
                      <input
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
               
              </scroll-view>
            </scroll-view>
          </center>
        
       </scroll-view>
       
      <keyboard-avoiding-view class="footer_container">
        <view class="footer" bg="primary.600" flex-direction="row">
          <text  ml="2" mt="3" color="light.50">Operaciones : </text>
          <button
            mt="2"
            mb="2"
            ml="2"
            size="sm"
            height="35px"
            bg="warning.600"
            :on-press="sumar"
          >
            sumar
          </button>
          <button
            mt="2"
            mb="2"
            ml="2"
            size="sm"
            height="35px"
            bg="warning.600"
            :on-press="resta"
          >
            Restar
          </button>
          <button
            mt="2"
            mb="2"
            ml="2"
            size="sm"
            height="35px"
            bg="warning.600"
            :on-press="Producto"
          >
            Multiplicar
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
      m: "",
      n: "",
      idF: "",
      idC: "",
      x: "",
      p: "",
      filasA: 0,
      columnaA: 0,
      filasB: 0,
      columnaB: 0,
      Matriz_A: [],
      Matriz_B: [],
      resultadoM:[],
      clave:0,
      Mclave:0,
    };
  },
  methods: {
    mostrar: function () {
      this.Matriz_A = [];
      this.Matriz_B = [];
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
    },

    sumar: function()
    {
      this.clave = 1;
      this.Mclave = 2;
      this.resultadoM =[];
      var contB = 1;
      var auxiliarB = [];
      var auxiliarc = [];
      this.filasB = Number(this.x);
      this.columnaB = Number(this.p);

      for (var i = 0; i < this.filasB; i++) {
        for (var j = 0; j < this.columnaB; j++) {
          

            auxiliarB.push({ id: contB, valor: ""+(Number(this.Matriz_A[i][j].valor)+Number(this.Matriz_B[i][j].valor))});
            console.log(auxiliarc);
            contB++;

        }

        this.resultadoM.push(auxiliarB);
        auxiliarB = [];

        
      }
            console.log(this.resultadoM);  
  },

    resta: function()
    {
      this.clave = 1;
      this.Mclave = 2;
      this.resultadoM =[];
      var contB = 1;
      var auxiliarB = [];
      var auxiliarc = [];
      this.filasB = Number(this.x);
      this.columnaB = Number(this.p);

      for (var i = 0; i < this.filasB; i++) {
        for (var j = 0; j < this.columnaB; j++) {
          

            auxiliarB.push({ id: contB, valor: ""+(Number(this.Matriz_A[i][j].valor)-Number(this.Matriz_B[i][j].valor))});
            console.log(auxiliarc);

            contB++;

        }

        this.resultadoM.push(auxiliarB);
        auxiliarB = [];

        
      }
            console.log(this.resultadoM);

      
    },
    Producto: function()
    {
      this.clave = 1;
      this.Mclave = 2;
      this.resultadoM =[];
      var contB = 0;
      var auxiliarB = [];

      this.filasA = Number(this.m);
      this.columnaA = Number(this.n);
      this.filasB = Number(this.x);
      this.columnaB = Number(this.p);

      for (var i = 0; i < this.filasA; i++) {
        for (var j = 0; j < this.columnaB; j++) {
            var rrr = [];
            var resu = [];
          for (let y = 0; y < this.filasB; y++) {


            rrr.push(parseInt(this.Matriz_A[i][y].valor)* parseInt(this.Matriz_B[y][j].valor));


            console.log("r");
            console.log(rrr);
            }
            var resultado = 0;
            for (let x = 0; x < rrr.length; x++) {
              
              resultado += rrr[x];
            }
            
            console.log(resu);
            auxiliarB.push({ id: contB, valor:""+(resultado)});
            contB++;

        }
        
        this.resultadoM.push(auxiliarB);
        auxiliarB = []; 
      }
            console.log(this.resultadoM);

      
    }

  },
};
</script>

