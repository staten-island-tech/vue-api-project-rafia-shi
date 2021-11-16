<template>
  <div id="app">
    <div class="test">
      API Project
     </div>
  </div>
</template>

<script>
export default{
  data(){
    return{
  
      datab: [],
    };
  },

  methods: {
    fetch('https://www.cheapshark.com/api/1.0/deals?storeID=1&upperPrice=15')
    .then(data =>)
</script>

<style>
body{
  background-color: teal;
  font-family: 'Courier New', Courier, monospace;
  font-size: 2rem;
  font-weight: bold;
  justify-content: center;
}
</style>
