// Todo List refs.
// https://qiita.com/moonglows76/items/358ef3cd1566c38ece3a
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
          <label v-bind:class="{ done: todo.isChecked }">
            <input type="checkbox" name="" id="" v-model="todo.isChecked">{{ todo.content }}
          </label>
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
      chk: false,
      addText: "",
      lastId: 1,
      todos: [
        { id:0, content:"test", isChecked: true }
      ]
    };
  },
  methods: {
    addItemData() {
      let item = {
        id: this.lastId,
        content: this.addText,
        isChecked: false,
      };
      this.todos.push(item);
    },
    onAdd(event) {
      if (!this.addText) {
        console.log("[ERR]addText is empty.");
        return;
      }
      this.lastId++;
      this.addItemData();
      this.addText = "";
      this.save();
    },
    onDelete(event) {
      console.log("onDelete");
      // クリックされたオブジェクトを操作
      this.item = this.todos.filter(function (item) {
        console.log(item.content);
        return item.isChecked === false;
      });
      this.save();
    },
    save() {
      localStorage.setItem('todos', JSON.stringify(this.todos));
    },
    load() {
      console.log('load');
      this.todos = JSON.parse(localStorage.getItem('todos'));
      if (!this.todos) {
      console.log(' No data');
        this.todos = [];
      }
      else {
        let i = this.todos.length - 1;
        this.lastId = thiss.todos[i].id;
      console.log(' last id ' + this.lastId);
      }
    },
    created: function() {
      console.log('created');
    },
    mounted: function () {
      console.log('mounted');
      this.load();
    }
  }
};
</script>

<style>
.todoContent {
  border: 1px solid white;
}
.done {
  text-decoration: line-through;
}
</style>
