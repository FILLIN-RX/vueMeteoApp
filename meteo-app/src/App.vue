
<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div class="app-meteo">
    <h1>🌦️ Ma météo</h1>

    <input v-model="ville" placeholder="Tape une ville..." />
    <button @click="chercherMeteo">Chercher</button>

    <!-- On affiche le composant MeteO -->
    <MeteOpp :meteo="meteo" />
  </div>
  
</template>

<script>

import MeteOpp from './components/MeteOpp.vue' 

export default {
  name: 'App',
  components: {
    MeteOpp
  },
  data() {
    return {
      ville: "",
      meteo: null
    }
  },
  methods: {
    async chercherMeteo() {
      const apiKey = "b5ad58a47cca36286c5eb09a98fb7bd7"
      const url = `https://api.openweathermap.org/data/2.5/weather?q=${this.ville}&units=metric&appid=${apiKey}&lang=fr`

      const response = await fetch(url)
      const data = await response.json()
      this.meteo = data
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
