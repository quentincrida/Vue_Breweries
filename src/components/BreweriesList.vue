<template lang="html">
  <div>
    <ul>
      <list-item v-for="(brewery, index) in breweries" :brewery="brewery" :key="index"></list-item>
    </ul>

  </div>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
  name: 'breweries-list',
  props: ['breweries'],



  components: {
    "list-item": ListItem
  }
}
</script>

<style>

.main-container {
  display: flex;
  justify-content: space-between;
}
</style>
