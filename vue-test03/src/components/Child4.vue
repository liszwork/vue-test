<template>
  <div id="child" class="content">
    <h3>Child4</h3>
    <button value="click" @click="$emit('hello')">parent message</button>
  </div>
</template>

<script>
export default {
  name: "Child3",
  data() {
    return {
      cnt: 0
    }
  },
  methods: {
    change(event) {
      const msgs = [ "hoge", "huga", "piyo" ];
      this.$parent.hoge = msgs[this.cnt];
      this.cnt++;
      if ( this.cnt >= msgs.length)
      {
        this.cnt = 0;
      }
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
