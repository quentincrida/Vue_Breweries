<template>
  <div id="app">
<h1>Breweries</h1>
  <div class="main-container">
  </div>
  </div>
</template>

<script>

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
