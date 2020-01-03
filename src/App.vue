<template>
  <div id="app">
    <h1>USA Breweries</h1>
    <div></div>

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
  components: {
    "breweries-list": BreweriesList,
    "brewery-detail": BreweryDetail
  },
  data() {
    return {
      breweries: [],
      selectedBrewery: null
    };

  },
  // methods: {
  //   breweriesList.sort(function(a, b) {
  //     var nameA = a.name.toUpperCase();
  //     var nameB = b.name.toUpperCase();
  //     if (nameA < nameB) {
  //       return -1;
  //     }
  //     if (nameA > nameB) {
  //       return 1;
  //     }
  //     return 0;
  //   })
 // },


  mounted() {
    fetch("https://api.openbrewerydb.org/breweries")
    .then(response => response.json())
    .then(breweries => this.breweries = breweries)


    eventBus.$on('brewery-selected', (brewery) =>
    {
      console.log('within $on', brewery);
      this.selectedBrewery = brewery
  })
},




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
