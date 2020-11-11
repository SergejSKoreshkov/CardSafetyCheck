<template>
  <div id="app">
    <Card />
  </div>
</template>

<script>
import Card from './components/Card.vue'

export default {
  name: 'App',
  components: {
    Card
  }
}
</script>

<style>
 body, html {
   margin: 0;
   padding: 0;
 }

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #263238;
  background-image: url('./assets/back.jpg');
  background-position: center;
  background-size: cover;
  height: 100vh;
  width: 100vw;
}
</style>
