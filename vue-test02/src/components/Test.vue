<template>
  <div id="test">
    <div class="content">
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
    </div>
    <div class="content">
      <!-- 切替ボタン -->
      <button @click="click">toggle show</button>
      <!-- 切替チェック -->
      <input type="checkbox" id="isShowChk" v-model="show">
      <label for="isShowChk">{{ show }}</label>
      <!-- falseでdisplay:noneとなる -->
      <p v-show="show">item1</p>
      <!-- falseで要素が消される -->
      <p v-if="show">item2</p>
    </div>
    <div class="content">
      <input type="type" v-model="message">
      <input @input="onInput" />
      <p>==> {{ message }}</p>
    </div>

    <div class="content">
      <input type="type" v-model="testmsg">
      <p>:: {{ testmsg }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Test",
  data() {
    return {
      testmsg: "",
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
};
</script>

<style>
.content {
  border: 3px dashed #AAF;
  margin: 5px;
  padding: 5px;
}
</style>
