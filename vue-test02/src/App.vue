<template>
  <div id="app">
    <img id="logo" src="./assets/logo.png">
    <Test/>
  </div>
</template>

<script>
import Test from './components/Test'

export default {
  name: 'App',
  components: {
    Test,
  }
}
</script>

<style>
body, div * {
  /* background-color: #333;
  color: #CCC; */
}
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
