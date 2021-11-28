<template>
  <div class="home">
    <PkmnList :id="20" :offset="0" />
  </div>
</template>

<script>
import PkmnList from "../components/PkmList";
export default {
  name: "Home",
  components: {
    PkmnList,
  },
};
</script>
