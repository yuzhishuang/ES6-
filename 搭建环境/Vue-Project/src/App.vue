<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld/>
    <ArrayContent/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import ArrayContent from './components/ArrayContent'

export default {
  name: 'app',
  components: {
    HelloWorld,
    ArrayContent
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
