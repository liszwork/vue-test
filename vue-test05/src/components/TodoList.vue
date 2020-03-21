<template>
  <div class="content">
    <h1>Todo list</h1>
    <div id="addTodoForm">
      <input type="text" v-model="addText" />
      <button @click="onAdd">add</button>
    </div>
    <div id="todoContents">
      <ul>
        <li class="todoContent" v-for="(todo, index) in todos" :key="todos.content">
          <div>{{ todo.id }} - {{ todo.content }}</div>
          <button @click="onComplet">complet</button>
          <button @click="onDelete">delete</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  data() {
    return {
      addText: "",
      lastId: 0,
      todos: [
        { id:0, content:"test" }
      ]
    };
  },
  methods: {
    onAdd(event) {
      if (!this.addText) {
        console.log("[ERR]addText is empty.");
        return;
      }
      this.lastId++;
      let addItem = {
        id: this.lastId,
        content: this.addText
      };
      this.todos.push(addItem);
      this.addText = "";
    },
    onComplet(event) {
      console.log("onComplet")
    },
    onDelete(event) {
      console.log("onDelete")
    },
  }
};
</script>

<style>
.todoContent {
  border: 1px solid white;
}
</style>
