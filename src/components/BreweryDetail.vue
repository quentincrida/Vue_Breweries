<template lang="html">
  <div v-if='brewery'>
    <h3>{{brewery.name}}</h3>
    <p>Brewery Type: {{brewery.brewery_type}}</p>
    <p>City: {{brewery.city}}</p>
    <p>State: {{brewery.state}}</p>
</div>
</template>

<script>
export default {
  name: 'brewery-detail',
  props: ['brewery']
}
</script>

<style lang="css" scoped>
</style>
