<template>
  <div class="home">
    
    <GameList :id="20" :offset="0" />
  
  </div>
</template>

<script>
import GameList from "../components/GameList";
export default {
  name: "Home",
  components: {
   GameList,
  },
};
</script>
