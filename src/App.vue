<template>
  <div id="app">
    <h1>USA Breweries</h1>
      <div class="main-container">
        <breweries-list :breweries='breweries'></breweries-list>
        <brewery-detail :brewery='selectedBrewery'></brewery-detail>

      </div>
  </div>
</template>

<script>
import { eventBus } from './main.js'
import BreweriesList from './components/BreweriesList.vue';
import BreweryDetail from './components/BreweryDetail.vue';


export default {
  name: 'app',
  data() {
    return {
      breweries: [],
      selectedBrewery: null
    };

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
    "brewery-detail": BreweryDetail
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
