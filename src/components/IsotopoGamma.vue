<template>
  <div class="mx-3">
    <div class="row">
      <div class="">
        <h1 class="text-center font-bold underline text-2xl">
          ELEMENTOS UTILES PARA EL METODO K0
        </h1>
        <input
          type="text"
          v-model="buscar"
          class="rounded border-2 border-black m-0"
          placeholder="Ejemplo: Ar"
        />
      </div>
    </div>

    <div class="mt-3 space-y-5">
      <div class="" v-for="element in elements" v-bind:key="element.code">
        <div class="">
          <!-- <img
            class="card-img-top"
            v-bind:src="'img/' + item.img"
            v-bind:alt="item.nombre"
          /> -->
          <div class="flex space-x-2">
            <div class="w-14 text-sm pt-2">
              <sup>{{ element.a }}</sup
              >{{ element.simbolo
              }}<sup>{{
                states.filter((e) => e.code == element.state)[0].state
              }}</sup>
            </div>
            <div class="w-52">
              <span>Estado:</span>
              {{ states.filter((e) => e.code == element.state)[0].comment }}
            </div>
            <div class="w-60" v-if="element.vidaMedia != 'stbl'">
              <span class="font-semibold"
                >Vida media ({{ element.vidaMediaUnit }}):</span
              >
              {{ element.vidaMedia }} &plusmn;
              {{ element.vidaMediaErr }}
            </div>
            <div class="w-60" v-else>
              <span class="font-semibold">Elemento Estable</span>
            </div>
            <div class="w-60"><span>Referencia:</span> {{ element.ref }}</div>
            <button class="rounded border-2 border-black p-1">Detalles</button>
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
<style scoped></style>
