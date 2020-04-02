<template>
  <div id="child5" class="content">
    <h3>Child5</h3>
    <p>{{ msg }}</p>
    <input type="text" name="input" v-model="inputText">
    <button @click="onClickButton">click</button>
  </div>
</template>

<script>
export default {
  name: "Child5",
  props: ["msg"],
  data() {
    return {
      inputText: "",
    };
  },
  methods: {
    onClickButton(event) {
      this.$emit('parentFunc', this.inputText);
    },
  },
};
</script>

<style>
#child5 {
  background: #AAC;
}
.content {
  border: 1px dashed #ABF;
  margin: 5px;
  padding: 5px;
}
</style>
