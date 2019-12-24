<template>
  <div id="app">
<h1>USA Micro Breweries</h1>
  <div class="main-container">
    <ul>
      <!-- <li v-for="brewery in breweries">{{breweries}}</li> -->

    <breweries-list :breweries='breweries'></breweries-list>
  </ul>

  </div>
  </div>
</template>

<script>
import { eventBus } from './main.js'
import BreweriesList from './components/BreweriesList.vue';


export default {
  name: 'app',
  data() {
    return {
      breweries: [],
      selectedBrewery: null
    };

  },
  computed: {

  },

  mounted() {
    fetch("https://api.openbrewerydb.org/breweries")
    .then(response => response.json())
    .then(breweries => this.breweries = breweries)


    eventBus.$on('selected-brewery', (brewery) =>
    {
      this.selectedBrewery = brewery
  })
},

  components: {
    "breweries-list": BreweriesList,
  }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
