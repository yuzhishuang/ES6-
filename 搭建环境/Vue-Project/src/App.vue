<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld/>
    <ArrayContent/>
    <FunctionContent/>
    <setContent />
    <generatorContent />
    <promiseContent />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import ArrayContent from './components/ArrayContent'
import FunctionContent from './components/FunctionContent'
import setContent from './components/setContent'
import generatorContent from './components/generatorContent'
import promiseContent from './components/promiseContent'

export default {
  name: 'app',
  components: {
    HelloWorld,
    ArrayContent,
    FunctionContent,
    setContent,
    generatorContent,
    promiseContent
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
