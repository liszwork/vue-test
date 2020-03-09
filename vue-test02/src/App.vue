<template>
  <div id="app">
    <img id="logo" src="./assets/logo.png">
    <p>==> {{ message }}</p>
    <input type="type" v-model="message">
    <QA/>
    <Test/>
    <HelloWorld/>
  </div>
</template>

<script>
import QA from './components/QA'
import Test from './components/Test'
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  data() {
    return {
      message: "hogehoge"
    }
  },
  components: {
    QA,
    Test,
    HelloWorld
  }
}
</script>

<style>
body, div * {
  background-color: #333;
  color: #CCC;
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
