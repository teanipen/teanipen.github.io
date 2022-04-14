<template>
  <div class="container cont">
    <div class="row">
      <div class="col-md-12">
        <h1>Decay lines of the elements</h1>

        <input
          type="text"
          v-model="buscar"
          class="form-control"
          placeholder="Ejemplo: Ar"
        />
      </div>
    </div>

    <div class="row mt-3">
      <div class="col-md-4" v-for="item in items" v-bind:key="item.code">
        <div class="card mb-3">
          <!-- <img
            class="card-img-top"
            v-bind:src="'img/' + item.img"
            v-bind:alt="item.nombre"
          /> -->
          <div class="card-body">
            <h3 class="card-title mb-3">
              <sup>{{ item.a }}</sup
              >{{ item.emisor
              }}<sup>{{ states.filter((e) => e.code == item.s)[0].state }}</sup>
            </h3>
            <p class="card-text">
              <strong>Isótopo Fuente:</strong> {{ item.target }} -
              {{ item.a - 1 }}
            </p>
            <p class="card-text"><strong>E(KeV)</strong> {{ item.gamma }}</p>
            <p class="card-text">
              <strong>factor k0:</strong> {{ item.k0 }} &#177; {{ item.dk0 }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import datos from "../assets/json/elementos.json";
import states from "../assets/json/states.json";

export default {
  // Exporto mi componente 'Pokemones'
  name: "ElementosK0s",
  props: {
    msg: String,
  },

  // declaro el elemento buscar
  data() {
    return {
      buscar: "",
      states: states,
    };
  },

  // Creo un método llamado 'items' y obtengo los datos de los pokemones
  // Asimismo filtro la búsqueda de los pokemones con el método filter()
  computed: {
    items() {
      return datos.filter((item) => {
        return item.emisor.toLowerCase().includes(this.buscar.toLowerCase());
      });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/**/
</style>
