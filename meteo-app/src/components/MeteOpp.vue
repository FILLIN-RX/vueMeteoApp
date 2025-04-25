<!-- src/components/Meteo.vue -->
<template>
    <div v-if="meteo && meteo.main && meteo.weather">
      <p>📍 Ville : {{ meteo.name }}</p>
      <p>🌡️ Température : {{ meteo.main.temp }} °C</p>
      <p>🌥️ Météo : {{ meteo.weather[0].description }}</p>
  
      <!-- Icône météo -->
      <img
        :src="`https://openweathermap.org/img/wn/${meteo.weather[0].icon}@2x.png`"
        :alt="meteo.weather[0].description"
      />
    </div>
  </template>
  
  <script>
  export default {
    name: "Meteo",
    props: {
      meteo: Object
    }
  }
  </script>
  
  <style scoped>
  img {
    width: 80px;
    height: 80px;
  }
  </style>
  
