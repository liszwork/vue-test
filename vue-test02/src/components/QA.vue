<template>
  <!-- <div id="question">
    <input type="checkbox" id="jack" v-model="checkedNames">
    <label for="jack">Jack</label>
    <input type="checkbox" id="John" v-model="checkedNames">
    <label for="John">John</label>
    <input type="checkbox" id="Mike" v-model="checkedNames">
    <label for="Mike">Mike</label>
    <br>
    <span>Checked names: {{ checkedNames }}</span>
  </div> -->
  <div id="question">
    <p>QA vue</p>
    <p>{{ data }}</p>
  </div>
</template>

<script>
export default {
  name: 'QA',
  data() {
    return {
      data: "hihi"
    }
  }
}
</script>

<style>
</style>
