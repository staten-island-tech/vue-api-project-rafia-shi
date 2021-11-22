<template>
  <div id="app">
    <div class="test">API Project</div>
    <div class="data-goes-here" v-for=" method in methods" :key="method">Data {{method.apiCall}}</div>
  </div>
</template>

<script>
export default {
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
  
};
</script>

<style>
body {
  background-color: teal;
  font-family: "Courier New", Courier, monospace;
  font-size: 2rem;
  font-weight: bold;
  justify-content: center;
}
</style>
