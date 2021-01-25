<template>
  <div id="app">
    <SpoilGotApp/>
  </div>
</template>

<script>
import SpoilGotApp from './components/SpoilGotApp.vue'


export default {
  name: 'App',
  components: {
    SpoilGotApp
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
