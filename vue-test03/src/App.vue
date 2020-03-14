<template>
  <div id="app">
    <div class="content">
      <h2>データを直接渡す</h2>
      <Child message="Message: Parent to Child" />
    </div>
    <div class="content">
      <h2>変数を渡す</h2>
      <input type="text" v-model="text">
      <Child2 :message="text" />
    </div>
    <div class="content">
      <h2>子→親</h2>
      <p>{{ c3data }}</p>
      <Child3 />
      <p>{{ hoge }}</p>
    </div>
    <div class="content">
      <h2>子→親メソッド</h2>
      <button @click="hello">click</button>
      <Child4 />
    </div>
  </div>
</template>

<script>
import Child from './components/Child'
import Child2 from './components/Child2'
import Child3 from './components/Child3'
import Child4 from './components/Child4'

export default {
  name: 'App',
  components: {
    Child,
    Child2,
    Child3,
    Child4,
  },
  data() {
    return {
      text: 'Hello',
      c3data: 'msg',
      hoge: "-",
    }
  },
  methods: {
    hello() {
      console.log("Hello, i'm App.vue!");
    }
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
.content {
  border: 3px dashed #AAF;
  margin: 5px;
  padding: 5px;
}
</style>
