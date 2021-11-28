<template>
  <div>
    <h1>TEST</h1>
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
h1 {
  font-size: 5rem;
  color: black;
}
li {
  color: black;
}
</style>
