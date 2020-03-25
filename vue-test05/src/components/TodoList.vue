/*-------------------------------------------------------
Todo List refs.
https://qiita.com/moonglows76/items/358ef3cd1566c38ece3a
Browser local storage check
https://qiita.com/k_yumoto/items/d2026128a08ed8fab22c
Local storage
https://qiita.com/shingorow/items/97c265d4cab33cb13b6c
CSS - list
https://saruwakakun.com/html-css/reference/ul-ol-li-design
CSS - checkbox
https://kodocode.net/design-css-checkbox/
-------------------------------------------------------*/
<template>
  <div class="content">
    <div class="header">
      <h1>My Todos</h1>
    </div>

    <div class="input-form">
      <div id="add-todo-form">
        <input type="text" v-model="addText" />
        <button @click="onAdd">add Todo</button>
      </div>
      <div class="function-menu">
        <button @click="onDelete">delete checked Todos</button>
        <button @click="onClear">clear all Todos</button>
      </div>
    </div>

    <div id="todo-contents">
      <ul class="todo">
        <li class="todo-content" v-for="(todo, index) in todos" :key="todos.id">
          <label class="todo-checkbox" v-bind:class="{ done: todo.isChecked }">
            <input type="checkbox" v-model="todo.isChecked" />
              {{ todo.content }}
          </label>
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
      lastId: 0,
      todos: []
    };
  },
  methods: {
    addItemData() {
      let item = {
        id: this.lastId,
        content: this.addText,
        isChecked: false
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
      this.todos = this.todos.filter(function(item) {
        // isCheckedがfalseのみフィルタリングして、itemにセットし直してる？
        return item.isChecked === false;
      });
      this.save();
    },
    onClear(event) {
      this.todos = [];
      this.lastId = 0;
      this.save();
    },
    save() {
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
    load() {
      console.log("load");
      this.todos = JSON.parse(localStorage.getItem("todos"));
      if (!this.todos.length) {
        console.log(" No data");
        this.todos = [];
      } else {
        console.log(" find data");
        let i = this.todos.length - 1;
        this.lastId = this.todos[i].id;
        console.log(" last id " + this.lastId);
      }
    }
  },
  created() {
    console.log("created");
  },
  mounted() {
    console.log("mounted");
    this.load();
  }
};
</script>

<style>
.content {
  margin-left: 30px;
  margin-right: 30px;
}
ul {
  padding: 0;
}
.todo-content {
  position: relative;
  padding: 0.5em 0.5em 0.5em 0.5em;
  margin-bottom: 5px;
  line-height: 1.5;
  background: #505050;
  border-radius: 15px 0px 0px 15px;
  list-style-type: none!important;
  text-align: left;
}
.todo-content:before {
  display: inline-block;
  vertical-align: middle;
}
.todo-content:hover {
  background: #666;
}
label {
  background: #505050;
  color: #dbebf8;
}
.todo-content {
  border: 1px solid white;
}

.done {
  text-decoration: line-through;
}
</style>
