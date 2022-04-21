<template>
  <MyHeader></MyHeader>
  <router-view />
</template>

<script>
import MyHeader from "./components/MyHeader.vue";

export default {
  components: {
    MyHeader,
  },
};
</script>

<style>
@import "./css/reset.css";
html,
body {
  height: 100%;
}
#app {
  height: 100%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}


</style>
