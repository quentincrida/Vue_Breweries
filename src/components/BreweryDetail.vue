<template lang="html">
  <div v-else-if='brewery'>
    <h3>Brewery Name: </h3>
    <p>Brewery Type: </p>
    <p>City: </p>
    <p>State: </p>
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
