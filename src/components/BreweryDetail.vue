<template lang="html">
  <div v-if='brewery'>
    <h3>{{brewery.name}}</h3>
    <p>Brewery Type: {{brewery.brewery_type}}</p>
    <p>City: {{brewery.city}}</p>
    <p>State: {{brewery.state}}</p>
    <p>Website: {{brewery.website_url}}</p>
    <button v-on:click="addTasted">Have tasted this one</button>
</div>
</template>

<script>
export default {
  name: 'brewery-detail',
  props: ['brewery'],

  methods: {
    addTasted: function() {
    eventBus.$emit("tasted-added", this.brewery);
    }
  }
};
</script>

<style lang="css" scoped>
</style>
