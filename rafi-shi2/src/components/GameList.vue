<template>
  <div id="app">
    <div class="test">API Project</div>
    <ul class="game-table">
      <li class="game-list"
       v-for="game in games" 
       :key="game.title"
       > 
         {{game.title}}

       </li>  
  </ul>

   
  </div>
</template>

<script>
/*export default {
  data() {
    return {
      datab: [],
    };
  },
  methods: {
    apiCall: async function () {
      try {
        const response = await fetch ('https://www.cheapshark.com/api/1.0/deals?storeID=1&upperPrice=15')
        const data = await response.json
        console.log(data)
        }
           catch (error) {
    console.log(error);
    alert("Something went wrong");
  }
  this.apiCall.push(datab)
        }
      
    }
  
};*/


export default {
  name: "GameList",
  data(){
    return{
      games: []
    };
  },
  props:[],
  created: function(){
    this.fetchData();

  },
  methods: {
    fetchData: async function () {
      try {
        const result = await fetch (`https://www.cheapshark.com/api/1.0/deals?storeID=1&upperPrice=15`);
        const data = await result.json();
        console.log(data);
        this.games = data.results;
        
      } catch (error) {
        alert("Sorry, something went wrong! Contact Vinny Shi for help");
        
      }
    }
  }
}
</script>

<style>
body {
  background-color: teal;
  font-family: "Courier New", Courier, monospace;
  font-size: 2rem;
  font-weight: bold;
  justify-content: center;
}
.gameList{
  background: white;
  color: black;
}
</style>

