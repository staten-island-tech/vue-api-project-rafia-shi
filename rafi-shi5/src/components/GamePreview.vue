<template>
  <div>
    <router-link :to="gamePath" class="link">
      <div id="query">
        {{ game.title }}
        <img class="games" :src="sprite" alt="" />
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
.link {
  color: #b1b3c9;
  text-decoration-line: none;
  font-size: 1rem;
  font-family: "Courier New", Courier, monospace;
  display: table-row-group;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
}

.games {
  margin-top: 0.5rem;
  height: 18.5rem;
  width: 80%;
}
</style>

