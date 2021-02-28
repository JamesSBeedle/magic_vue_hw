<template>
    <article>
        <ul>
        <card-list-item v-for="(card, index) in cards" :card="card" :key="index">{{card.name}}</card-list-item>
        </ul>
    </article>
  
</template>

<script>
import cardListItem from "./CardListItems.vue"

export default {
    name: "card-list",
    props:['cards'],
    components: {
        'card-list-item': cardListItem
    }

}
</script>

<style>
ul{
    list-style-type: none;
    font-size: 30px;
    padding:0;
}
</style>