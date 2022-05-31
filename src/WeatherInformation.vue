<template>
      <div class="weather-wrap" v-if="information">
        <div class="location-box">
          <div class="location"> {{information.name}}, {{information.sys.country}} </div>
          <div class="date"> {{getDate()}} </div>
        </div>
        <div class="weather-box">
          <div class="temp"> {{Math.round(information.main.temp)}}°C </div>
          <div class="weather"> {{information.weather[0].main}} </div>
        </div>
        <div class="date" style="color:aliceblue;"> {{currentTime}} </div>
      </div>
</template>

<script>
export default {
  data() {
    return {
      currentTime: null,
      intervalID: null
    }
  },
  props: {
    information:{
      type:[Object, null],
      required:true
    }
  },
  /*
  created() {
    this.intervalID = setInterval(this.refreshDate, 1000)
  },
  unmounted() {
    clearInterval(this.intervalID)
  },*/
  methods: {
    getDate(){
      return new Date().toDateString();
    },
    /*refreshDate(){
      if(this.information){
        this.currentTime = new Date().toLocaleString('en-US', {timezone: this.information.timezone});
      } 
    }*/
  }
}
</script>

<style scoped>
.location-box .location {
  color: #FFF;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px  3px rgba(0,0,0,0.25);
}

.location-box .date {
  color: #FFF;
  padding-top: 10px;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}

.weather-box {
  text-align: center;
}

.weather-box .temp {
  display: inline-block;
  padding: 10px 25px;
  color: #FFF;
  font-size: 102px;
  font-weight: 900;
  text-shadow: 3px  6px rgba(0,0,0,0.25);
  background-color: rgba(255,255,255,0.25);
  border-radius: 16px;
  margin: 30px 0px;
  box-shadow: 3px  6px rgba(0,0,0,0.25);;
}

.weather-box .weather {
  color: #FFF;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px  6px rgba(0,0,0,0.25);
}
</style>