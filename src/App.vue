<template>
  <div id="app">
    <h1 class="title">Consultar datos</h1>
    <button v-on:click="fetch">Consultar</button>
    <div v-for="character of characters" v-bind:key="character.id">
      {{ character }}
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data: function() {
    return {
      characters: []
    };
  },
  methods: {
    fetch() {
      axios
        .get("https://rickandmortyapi.com/api/character")
        .then(res => {
          this.characters = res.data.results;
          console.log(res.data);
        })
        .catch(err => {
          console.log(err);
        });
    }
  }
};
</script>
