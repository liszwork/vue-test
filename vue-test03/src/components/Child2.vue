<template>
  <div id="child" class="content">
    <h3>Child2</h3>
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  name: "Child2",
  props: ["message"]
};
</script>

<style>
.content {
  border: 1px dashed #ABF;
  margin: 5px;
  padding: 5px;
}
</style>
