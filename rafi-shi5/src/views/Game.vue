<template>
  <div class="container">
    <div class="card">
      <h2 class="name">{{ singleGame.external }}</h2>
      <img src="" alt="" />
      <h3 class=""></h3>
      <ul v-for="score in singleGame" :key="score" class="score">
        <li>
          <div>{{ score.external }}</div>
        </li>
        <li v-for="deal in singleGame" :key="deal" class="price">
          <div>Price: ${{ deal.cheapest }}</div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      singleGame: {},
      score: {},
      dealRating: {},
    };
  },
  beforeMount: function () {
    this.fetchData2();
  },
  methods: {
    fetchData2: async function () {
      try {
        const result = await fetch(
          `https://www.cheapshark.com/api/1.0/games?steamAppID=${this.$route.params.steamAppID}`
        );
        const singleGame = await result.json();
        this.singleGame = singleGame;
        console.log(singleGame);
        this.score = this.singleGame.score;
        this.dealRating = this.singleGame.dealRating;
        return [this.singleGame, this.score, this.dealRating];
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style>
.score {
  background: navajowhite;
  color: purple;
  text-decoration: none;
}
</style>
