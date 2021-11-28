<template>
  <div>
    <h1>API Project</h1>
    <ul class="game-table">
      <li
        class="game-list-item"
        v-for="game in games" :key="game.title"
      >
        {{game.title}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "GameList",
  data() {
    return { games: [] };
  },
  created: function() {
    this.fetchData();
  },
  methods: {
    fetchData: async function() {
      try {
        const result = await fetch(`https://www.cheapshark.com/api/1.0/deals?storeID=1&upperPrice=15`
          
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
ul{
  list-style-type: none;
}
h1 {
  font-size: 2.5rem;
  font-family: 'Courier New', Courier, monospace;
  text-align: center;
  background-color: white;
  color: orange;
  
  padding: 1.3rem;
 
}
li {
  color: black;
  
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
  flex-direction: column;
  margin: 0 auto;
  justify-content: space-evenly;

}
.game-list-item{
  color: white;
  font-family: 'Courier New', Courier, monospace;
  border-radius: 1.5rem;
  font-size: 1rem;
  background-color: tomato;
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
