<template>
  <div id="app">
    <!-- Muestro el componente 'Pokemones' en el template de 'App.vue' -->
    <ElementosK0s />
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'

// Importo el componente 'Pokemones'
import ElementosK0s from "./components/IsotopoGamma.vue";

export default {
  name: "App",
  components: {
    ElementosK0s,
  },
};
</script>

<style>
/* #app {

} */
</style>
