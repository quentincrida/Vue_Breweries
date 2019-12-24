<template lang="html">
  <li v-on:click="handleClick">{{brewery.name}}</li>

</template>

<script>
import { eventBus } from "../main.js"

export default {
  name: 'list-item',
  props: ['brewery'],
  methods: {
    handleClick(){
      eventBus.$emit('brewery-selected', this.brewery)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
