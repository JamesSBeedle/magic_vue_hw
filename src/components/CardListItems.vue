<template>
  <article>
    <li v-on:click="handleClick">{{card.name}}</li>
    <hr>
  </article>
</template>

<script>
import { eventBus } from '@/main.js';
export default {
    name: "card-list-item",
    props:['card'],
    methods: {
      handleClick() {
        eventBus.$emit('selected-card', this.card)
      }
    }

}
</script>

<style>

</style>