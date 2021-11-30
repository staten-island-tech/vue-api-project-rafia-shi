<template>
  <div>
    <div><img src="../assets/steamlogo.png" alt=""></div>
    <h1>Welcome To Steam</h1>
    <div class="game-table">
      <div class="game-list-item" v-for="game in games" :key="game.title">
        <GamePreview :game="game" />
      </div>
    </div>
  </div>
</template>

<script>
import GamePreview from "./GamePreview.vue";
export default {
  name: "GameList",
  components: {
    GamePreview,
  },

  data() {
    return { games: [] };
  },
  props: ["id", "number"],
  created: function () {
    this.fetchData();
  },
  methods: {
    fetchData: async function () {
      try {
        const result = await fetch(
          `https://www.cheapshark.com/api/1.0/deals?storeID=1&upperPrice=15&pageSize=${this.id}&pageNumber=${this.number}`
        );
        const apiData = await result.json();
        this.games = apiData;
        console.log(apiData);
      } catch (error) {
        alert(error);
      }
    },
  },
};
</script>

<style>
h1 {
  font-size: 2.5rem;
  font-family: "Courier New", Courier, monospace;
  justify-content: center;
  background-color: #171a21;
  color: Black;
  padding: 1.5rem;
  padding-bottom: 1.65rem;
  
  
  
}
body {
  background-color: #040720;
  font-family: "Courier New", Courier, monospace;
  font-size: 2rem;
  font-weight: bold;
  justify-content: center;
  font-family: "Courier New", Courier, monospace;
}
.game-table {
  display: flex;
  flex-wrap: wrap;
  width: 80vw;
  margin: 0 auto;
  justify-content: space-between;
  vertical-align: middle;
  
}
.game-list-item {
  color:navy;
  font-family: "Courier New", Courier, monospace;
  border-radius: 1.5rem;
  width: 25%;
  height: 20rem;
  font-size: .5rem;
  background-color: #171a21;
  padding: 0.5rem;
  align-content: space-around;
  margin-bottom: 2rem;
  padding-bottom: 2rem;
  

 
}
.game-list-item:hover {
  transform: scale(1.1);
  transition: 0.3s all;
  cursor: pointer;
}
.price {
  margin: 0.5rem;
}
img{
height: 5rem;


  
  
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
