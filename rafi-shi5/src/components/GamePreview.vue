<template>
  <div>
    <router-link :to="gamePath" class="link">
      <div id="query">
        {{ game.title }}
        <img :src="sprite" alt="" />
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: "GamePreview",
  props: ["game"],
  data() {
    return {
      singleGame: {},
    };
  },
  mounted: function () {
    this.fetchData2();
    console.log(this.singleGame);
  },
  methods: {
    fetchData2: async function () {
      try {
        const result = await fetch(
          `https://www.cheapshark.com/api/1.0/deals?storeID=1&upperPrice=15${this.game.gameID}`
        );
        const singleGame = await result.json();
        this.singleGame = singleGame;
      } catch (error) {
        console.log(error);
      }
    },
  },
  computed: {
    sprite: function () {
      return `https://cdn.cloudflare.steamstatic.com//steam//apps//${this.game.steamAppID}//capsule_sm_120.jpg?t=1602794480`;
    },
    gamePath: function () {
      return `/game/${this.game.steamAppID}`;
    },
  },
};
//do .steamappid tomorrow
</script>

<style>
.query {
  margin-top: 2rem;
}
.link {
  color: whitesmoke;
  text-decoration-line: none;
  font-size: 2rem;
  font-family: "Courier New", Courier, monospace;
  

 
}
</style>
