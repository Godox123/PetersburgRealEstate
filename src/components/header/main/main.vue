<template>
  <div class="header">
    <Navigation></Navigation>
    <Func></Func>
  </div>
</template>

<script>
import Navigation from "../navigation/navigation.vue";
import Func from "../func/func.vue";

export default {
  name: "Header",
  components: {
    Navigation,
    Func,
  },
};
</script>

<style></style>
