<template>
  <div class="layout">
    <div class="layout__bd">
      <Header></Header>
      <Items></Items>
    </div>
  </div>
</template>

<script>
import Header from "./components/header/main/main.vue";
import Items from "./components/items/main/main.vue";

export default {
  name: "App",

  components: {
    Header,
    Items,
  },
};
</script>

<style>
.layout {
  background: #f7f6f4;
  width: 100%;
  min-height: 100vh;
}

.layout__bd {
  padding: 89px 99px 84px 100px;
  width: 1200px;
  margin: auto;
}
</style>
