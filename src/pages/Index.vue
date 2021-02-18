<template>
  <q-page class="flex column">
    <div class="col q-pt-lg q-px-md">
      <q-input
        v-model="search"
        placeholder="Search"
        dark
        borderless
        >

        <template v-slot:before>
          <q-icon
          @click="getLocation()"
            name="my_location" />
        </template>

        <template v-slot:append>
          <q-btn round dense flat icon="search" />
        </template>
      </q-input>
    </div>
    <template v-if="weatherData">
      <div class="col text-white text-center">
        <div class="text-h4 text-weight-light">
          Manchester
        </div>
        <div class="text-h6 text-weight-light">
          Rain
        </div>
        <div class="text-h1 text-weight-thin q-my-lg relative-position">
        <span>8</span>
        <span class="text-h4 relative-position degree">&deg;</span>
        </div>
      </div>
      <div class="col text-center">
        <img src="https://www.fillmurray.com/100/100" alt="Bill">
      </div>
    </template>
    <template v-else>
      <div class="col column text-center text-white">
        <div class="col text-h2 text-weight-thin">
          Quasar<br>Weather
        </div>
        <q-btn
          class="col"
          @click="getLocation()"
          flat>
          <q-icon
            left
            size="3em"
            name="my_location" />
          <div>Find my Location</div>
        </q-btn>
      </div>
    </template>


    <div class="col skyline"></div>
  </q-page>
</template>

<script>
import axios from 'axios'
export default {
  name: 'PageIndex',
  data(){
    return{
      search:'',
      weatherData: null,
      lat:null,
      lon:null,
      apiKey:'a1707abe12e4921a2be970863b972787',
      apiUrl:'https://samples.openweathermap.org/data/2.5/weather'
    }
  },
  methods:{
    getLocation(){
      navigator.geolocation.getCurrentPosition(position=>{
        console.log("My: ", position)
        this.lat= position.coords.latitude
        this.lon= position.coords.longitude
        this.getWeatherByCoords()

      })
    },
    getWeatherByCoords() {
      
       axios.get('https://www.google.com/').then(res=>{
        console.log("Res: ", res)
      })
      /* var xx = axios.get(`${this.apiUrl}?lat=${this.lat}&lon=${this.lon}&appid=${this.apiKey}`)
      console.log("X: ", xx) */
    }
  }
}
</script>

<style lang="sass">
  .q-page
    background: linear-gradient(to bottom, #136a8a, #267871) 
  .degree
    top: -44px
  .skyline
    flex:0 0 100px
    background: url('~assets/skyline.png')
    background-size: contain
    background-position: center bottom
</style>
