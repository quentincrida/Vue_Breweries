<template>
  <div id="app">
<h1>USA Breweries</h1>
  <div class="main-container">
    <!-- <ul>
      <li v-for="brewery in breweries">{{breweries}}</li>
    </ul> -->
    <breweries-list :breweries='breweries'></breweries-list>
  </div>
  </div>
</template>

<script>
import BreweriesList from './components/BreweriesList.vue';
import { eventBus } from './main.js'
// import BreweryDetail from './components/BreweryDetail.vue'

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
  },
  components: {
    "breweries-list": BreweriesList,
    // "brewery-detail": BreweryDetail
  }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
