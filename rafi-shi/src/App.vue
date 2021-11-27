<template>
  <div id="app">
    <div class="test">Crunchyvue</div>
    <h1 class="logo"></h1>
    <div class="data-goes-here">
      <button class="btn" @click="fetchData"> Click Me</button> 

    </div>
  </div>
</template>

<script>
export default {
  data() {
    return{ 
      datab:[]
    
    }
  },
  methods: {
fetchData() {
   fetch("https://www.cheapshark.com/api/1.0/deals?storeID=1&upperPrice=15")
       .then((response) => {
         if (response.ok) {
            return response.json();
         }
       })
       .then((data) => {
         console.log(data);
       }
       )},
  },
}

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
.btn{
  border-radius: 1.5rem;
  background-color: aquamarine;
  text-align: center;
  align-items: center;
}
</style>
