<template>
  <div id="app">
    <img class="logo" src="./assets/pokemon-logo.jpg" />
    <h1>PokeGuía</h1>

    <div>
      <label for="">Nombre:</label>
      <input type="text" v-model="nombreDelPokemon" />
      <button @click="clickBotonBuscar()">Buscar</button>
    </div>

    <pre>{{ pokemonQueSeTrajoDeInternet }}</pre>

    <ExampleFetch />
    <ExampleAxios />
  </div>
</template>

<script>
import ExampleFetch from "./components/ExampleFetch.vue";
import ExampleAxios from "./components/ExampleAxios.vue";

export default {
  components: { ExampleFetch, ExampleAxios },
  name: "App",
  data: () => ({
    nombreDelPokemon: "",
    pokemonQueSeTrajoDeInternet: null,
  }),
  methods: {
    clickBotonBuscar() {
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.nombreDelPokemon}`)
        .then((response) => {
          return response.json();
        })
        .then((loQueSeaQueMeTrajeDeInternet) => {
          this.pokemonQueSeTrajoDeInternet = loQueSeaQueMeTrajeDeInternet;
        });
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.logo {
  width: 50vh;
}
</style>
