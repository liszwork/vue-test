<template>
  <div id="app">
    <img id="logo" src="./assets/logo.png">
    <QA/>
    <HelloWorld/>
  </div>
</template>

<script>
import QA from './components/QA'
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  components: {
    QA,
    HelloWorld
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
#logo {
  width: 32px;
  height: auto;
  position: absolute;
  top: 0px;
  left: 0px;
}
</style>
