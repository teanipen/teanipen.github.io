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

    <div class="">
      <div class="" v-for="element in elements" v-bind:key="element.code">
        <div class="">
          <!-- <img
            class="card-img-top"
            v-bind:src="'img/' + item.img"
            v-bind:alt="item.nombre"
          /> -->
          <div class="flex-container">
            <div class="">
              <sup>{{ element.a }}</sup
              >{{ element.simbolo
              }}<sup>{{
                states.filter((e) => e.code == element.state)[0].state
              }}</sup>
            </div>
            <div class="">
              <strong>Estado:</strong>
              {{ states.filter((e) => e.code == element.state)[0].comment }}
            </div>
            <div v-if="element.vidaMedia != 'stbl'">
              <strong>Vida media ({{ element.vidaMediaUnit }}):</strong>
              {{ element.vidaMedia }} &plusmn;
              {{ element.vidaMediaErr }}
            </div>
            <div v-else><strong>Elemento Estable</strong></div>
            <div><strong>Referencia:</strong> {{ element.ref }}</div>
            <button>Detalles</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import elementos from "../assets/json/elementos.json";
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
    elements() {
      return elementos.filter((item) => {
        return item.elemento.toLowerCase().includes(this.buscar.toLowerCase());
      });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.flex-container {
  display: flex;
}
</style>
