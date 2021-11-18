<template>
  <div id="app">
    <div class="test">crunchyvue</div>
    <h1 class="logo"></h1>
    <div class="data-goes-here" v-for=" method in methods" :key="method"> {{method.api}}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      methods: {
        api: fetch(
          "https://anilist.co/api"
        )
          .then((data) => {
            return data.json();
          })
          .then((data) => {
            console.log(data);
          }),
      },
    };
  },
};
</script>

<style>
body {
  background-color: orange;
  font-family: "Courier New", Courier, monospace;
  font-size: 2rem;
  font-weight: bold;
  justify-content: center;
}
.test{
  text-align: center;
  background-color: white;
  color: orange;
  
  padding: 1.3rem;
 
}
.logo{
  background-image: url("./assets/Crunchyroll.png");
}
</style>
