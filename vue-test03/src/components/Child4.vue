<template>
  <div id="child" class="content">
    <h3>Child4</h3>
    <button value="click" @click="$emit('hello')">parent message</button>
    <button @click="callParentMethod">parent message</button>
  </div>
</template>

<script>
export default {
  name: "Child4",
  data() {
    return {
      cnt: 0
    }
  },
  methods: {
    callParentMethod(event) {
      this.$emit("hello");
    }
  }
};
</script>

<style>
.content {
  border: 1px dashed #ABF;
  margin: 5px;
  padding: 5px;
}
</style>
