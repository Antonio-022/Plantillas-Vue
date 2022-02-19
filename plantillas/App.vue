<template>
  <app-navigator></app-navigator>
</template>
<script>
import {
  createAppContainer,
  createStackNavigator,
} from "vue-native-router";
import plantilla1 from "./screens/plantilla1.vue";
import plantilla3 from "./screens/plantilla3.vue";
import plantilla2 from "./screens/plantilla2.vue";
import plantilla4 from "./screens/plantilla4.vue";
const StackNavigator = createStackNavigator(
  {
    option1 : plantilla1,
    option2 : plantilla2,
    option3 : plantilla3,
    option4 : plantilla4

  },
  {
    initialRouteName: 'option1',
    headerMode: "none"
  }
);
const AppNavigator = createAppContainer(StackNavigator);
export default {
  components: { AppNavigator },
}
</script>

