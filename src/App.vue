<template>
  <div id="app" :class="{'warm':weather && weather.main.temp > 16}">
    <main>
      <BaseSearchBox v-model="request" @enter="fetchWeather"></BaseSearchBox>
      <WeatherInformation :information="weather"></WeatherInformation>
    </main>
  </div>
</template>

<script>
import WeatherInformation from './WeatherInformation.vue'
import BaseSearchBox from './BaseSearchBox.vue'
const API_KEY = '6c009ee190c130d5aa752957a1aa043d'
const URL_BASE = 'https://api.openweathermap.org/data/2.5/'


export default {
  components:{
    WeatherInformation,
    BaseSearchBox
},
  name: 'App',
  data() {
    return {
      weather: null,
      request: ''
    }
  },
  methods: {
        fetchWeather(){
            fetch(`${URL_BASE}weather?q=${this.request}&units=metric&APPID=${API_KEY}`)
            .then(res => res.json())
            .then(result => {
                this.weather = result;
            });
        }
    }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'montserrat', sans-serif;
}

#app {
  background-image: url('./assets/cold-bg.jpg');;
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

#app.warm {
  background-image: url('./assets/warm-bg.jpg');
}

main {
  min-height: 100vh;
  padding: 25px;
  background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75));
}
</style>
