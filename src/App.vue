<template>
  <div id="app">
    <div class="hero is-white is-gradient is-bold">
      <div class="hero-body">
        <h1 class="title">
          <span class="has-text-success">R&M</span>
          <span class="subtitle">Personaje</span>
        </h1>
        <button class="button is-success is-rounded" v-on:click="fetch">
          Consultar
        </button>
      </div>
    </div>
    <div class="container">
      <div
        class="columns is-desktop is-mobile is-tablet is-multiline is-centered"
      >
        <div
          class="column is-12-meobile is-4-desktop is-4-tablet"
          v-for="character of characters"
          v-bind:key="character.id"
        >
          <div class="card">
            <div class="card-header">
              <img v-bind:src="character.image" v-bind:alt="character.name" />
            </div>
            <div class="card-content">
              <h3 class="title is-size-4">{{ character.name }}</h3>
              <button class="button title is-success is-rounded is-small">
                Ver más
              </button>

              <div class="h3"></div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <h1 class="title">Consultar datos</h1>

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
