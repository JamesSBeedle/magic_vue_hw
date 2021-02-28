<template>
  <section>
    <header>
      <section>
      <img src="https://i.pinimg.com/originals/68/df/3d/68df3d7f7fe51cb099b3874a53599191.png" alt="magit the gathering logo">  
      </section>
      <section>
      <h1> Version 1 card Information </h1>

      </section>
    </header>
  
    <main>
      <section id="list">  
        <card-list :cards="cardList"></card-list>
      </section>
      <section id="details">
        <card-details :card="selectedCard"></card-details>
      </section>
    </main>
  </section>
</template>

<script>
import CardList from "@/components/CardList.vue";
import CardDetails from "@/components/CardDetails.vue"


import { eventBus } from "@/main.js"

export default {
  name: 'App',
  data () {
    return {
      cardList: [],
      selectedCard: null,
      
    }

  },
  components: {
   'card-list' : CardList,
   'card-details': CardDetails,
  },

  methods:{
    getCardList() {
      fetch("https://api.magicthegathering.io/v1/cards")
      .then((res) => res.json())
      .then((data) => this.cardList = data.cards)
    },
    getSelectedCard(url) {
      fetch(url)
        .then((res) => res.json())
        .then((data) => (this.selectedCard = data));
    }

    
  },

  
  mounted () {
    this.getCardList();

    eventBus.$on('selected-card', (card) => {
      this.selectedCard = card
    });
    eventBus.$on('selected-card', (card) => {
      this.getSelectedCard(card, url)
    });
  },
}
</script>

<style>
*{
  box-sizing: border-box;
}
body{
  margin:0;
  padding:10px;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  text-align: center;
  background-color: black;
  color: white;
}
main{
  display:grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 10px;
  height: 550px;
}
#list{
  border:5px inset lightgray;
  height: 100%;
  overflow-y: scroll;
  padding:10px;
  
  
}
#details{
  border:5px inset lightgray;
  height: 100%;
  overflow-y: scroll;
  
}
img{
  height:250px;
  width:auto;
}
header{
  display:grid;
  grid-template-columns: 1fr 1fr;
  justify-content:center;
  align-items:center;
}
header > section > h1{
  
  font-size: 50px;

}


</style>
