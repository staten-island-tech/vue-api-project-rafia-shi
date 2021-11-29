<template>
  <div>
    <h1>API Project</h1>
    <div class="game-table">
      <div
        class="game-list-item"
        v-for="game in games" :key="game.title" 
      >
      <p class="api-data" > {{game.title}} </p>
       <p class="price"> $ {{game.salePrice}}</p>
       


      <GamePreview :game="game" /></div>
    </div>
  </div>
</template>

<script>
import GamePreview from "./GamePreview.vue";
export default {
  name: "GameList",
  components:{
    GamePreview,
  },

  data() {
    return { games: [] };
  },
  props:["id","number"],
  created: function() {
    this.fetchData();
  },
  methods: {
    fetchData: async function() {
      try {
        const result = await fetch(`https://www.cheapshark.com/api/1.0/deals?storeID=1&upperPrice=15&pageSize=${this.id}&pageNumber=${this.number}`
          
        );
        const apiData = await result.json();
        this.games = apiData;
        console.log(apiData);
      } catch (error) {
        alert(error);
      }
    },
  },
  computed:{
    sprite: function(){
      return this.games.thumb;
    }
  }
};
</script>

<style>
h1 {
  font-size: 2.5rem;
  font-family: 'Courier New', Courier, monospace;
  text-align: center;
  background-color: white;
  color: orange;
  
  padding: 1.3rem;
  opacity: .8;
 
}
body {
  background-color: orange;
  font-family: "Courier New", Courier, monospace;
  font-size: 2rem;
  font-weight: bold;
  justify-content: center;
  font-family: 'Courier New', Courier, monospace;
}
.game-table{
  display: flex;
  flex-wrap: wrap;
  width: 80vw;
  margin: 0 auto;
  justify-content: space-between;


}
.game-list-item{
  color: white;
  font-family: 'Courier New', Courier, monospace;
  border-radius: 1.5rem;
  width: 15%;
  height: 4rem;
  font-size: 1rem;
  background-color: tomato;
  padding: .5rem;
}
.game-list-item:hover{
  transform: scale(1.2);
  transition: .3s all ;
  cursor: pointer;
}
.price{
  margin: .5rem;
}
/*.test{
  text-align: center;
  background-color: white;
  color: orange;
  
  padding: 1.3rem;
 
}
.logo{
  background-image: url("./assets/Crunchyroll.png");
}
.btn{
  border-radius: 1.5rem;
  background-color: aquamarine;
  text-align: center;
  align-items: center;
}*/
</style>
