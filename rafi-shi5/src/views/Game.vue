<template>
  <div class="container">
    <div class="card">
      <h2 class="name">{{ singleGame.title }}</h2>
      <img src="" alt="" />
      <h3 class=""></h3>
      <ul>
        <li v-for="score in score" :key="score" class="score">
          <div>{{ score.metacriticScore }}</div>
        </li>
        <li v-for="deal in dealRating" :key="deal">
          <div>{{ deal.dealRating }}/10</div>
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
    console.log(this.$route.params.steamAppID)
  },
  methods: {
    fetchData2: async function () {
      try {
        const result = await fetch(
          
          `https://www.cheapshark.com/api/1.0/games?id=${this.$route.params.id}`
        );
        const singleGame = await result.json();
        this.singleGame = singleGame[0];
        this.score = this.singleGame.score;
        this.dealRating = this.singleGame.dealRating;
          console.log(this.singleGame)
        /* return [this.singleGame, this.score, this.dealRating] */
      
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style>
.score {
  background: orchid;
  color: aliceblue;
}
</style>
