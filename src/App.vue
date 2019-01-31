<template>
  <div id="app">
    <h1 class="title">Consultar datos</h1>
    <button v-on:click="fetch">Consultar</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data: function(){
    return {
      characters []
    };

  },
  methods: {
    fetch() {
      let result = axios
      .get("https://rickandmortyapi.com/api/character")
      .then(res => {
        this.characters = res.data.result;
        console.log(res.data);
      })
      .catch(err => {
        console.log(err);
      });
    }
  }
};
</script>
