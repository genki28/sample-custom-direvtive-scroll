// App.vue
<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    // HelloWorldから変更
    <Main/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWrold.vue'
import Main from './components/Main.vue'

export default {
  name: 'app',
  components: {
    // HelloWorld
    Main
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
