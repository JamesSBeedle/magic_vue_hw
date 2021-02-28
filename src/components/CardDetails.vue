<template>
  <article>
      <h2>Name:</h2>
      <h3>{{card.name}}</h3>
      <h2>Colour:</h2>
      <h3>{{card.colors[0]}}</h3>
      <h2>Mana Cost:</h2>
      <h3> {{card.manaCost}}</h3>
      <h2>Type:</h2>
      <h3>{{card.type}}</h3>
      <h2>Rarity:</h2>
      <h3>{{card.rarity}}</h3>
      <h2>Card Image:</h2>
      <img :src="card.imageUrl" alt="card image"/>
      
      
     
  </article>
</template>

<script>
export default {
  name: "card-details",
  props: ['card']
}
</script>

<style>
article > h2{
  font-size: 20px;
  color:grey;
  margin:0;
}
article > h3{
  font-size:30px;
  margin:25px;
}
</style>