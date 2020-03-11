<template>
  <div id="app">
    <ul>
      <li v-for="item in items" :key="item.message">
        {{ item.number }} - {{ item.message }}
      </li>
    </ul>
    <ul>
      <li v-for="(item, index) in items" :key="item.message">
        {{ parentMessage }}{{ index }} - {{ item.message }}
      </li>
    </ul>

    <input type="text" v-model="addText">
    <input type="button" @click="onAddText" value="add">

    <hr>
    <img id="logo" src="./assets/logo.png">
    <!-- 切替ボタン -->
    <button @click="click">toggle show</button>
    <!-- 切替チェック -->
    <input type="checkbox" id="isShowChk" v-model="show">
    <label for="isShowChk">{{ show }}</label>
    <!-- falseでdisplay:noneとなる -->
    <p v-show="show">item1</p>
    <!-- falseで要素が消される -->
    <p v-if="show">item2</p>

    <hr>
    <p>==> {{ message }}</p>
    <input type="type" v-model="message">
    <!-- <input @input="onInput" /> -->
    <QA/>
    <Test/>
  </div>
</template>

<script>
import QA from './components/QA'
import Test from './components/Test'

export default {
  name: 'App',
  data() {
    return {
      message: "hogehoge",
      show: "true",
      parentMessage: '★',
      items: [
        { number: 1, message: 'hoge' },
        { number: 2, message: 'huga' },
      ],
      addText: "",
    }
  },
  methods: {
    onAddText(event) {
      const item = this.items[this.items.length - 1];
      const number = item.number + 1;
      const message = this.addText;
      this.items.push({ number, message });
    },
    click(event) {
      this.show = !this.show;
    }
    // これがv-modelの中身
    // onInput(event) {
    //   const text = event.target.value;
    //   this.message = text;
    // }
  },
  components: {
    QA,
    Test,
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
