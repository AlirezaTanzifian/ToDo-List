<template>
  <div id="app">
    <Home></Home>
  </div>
</template>

<script>
import Home from "./components/Home.vue";

export default {
  components:{
    Home
  }

}
</script>

<style>
#app {
  color: white;
  height: 100vh;
  background: linear-gradient(to left, #283593, #1976d2);
  font-family: "Josefin Sans", sans-serif;
  padding: 3rem;
}
</style>
