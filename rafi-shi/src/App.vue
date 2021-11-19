<template>
  <div id="app">
    <div class="test">API Project</div>
    <div class="data-goes-here" v-for=" method in methods" :key="method">Data {{method.api}}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      datab: [],
    };
  },
  methods: {},
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
