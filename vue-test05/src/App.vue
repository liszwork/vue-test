<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->

    <div v-if="currentPage ===  0">
      <h1>Main page</h1>
      <ul>
        <li>
          <button class="menu-button" name="1" @click="selectedMenu">tick tack toe</button>
        </li>
        <li>
          <button class="menu-button" name="2" @click="selectedMenu">Todo List</button>
        </li>
      </ul>
    </div>

    <!-- Pages -->
    <TickTackToe v-if="currentPage === 1" />
    <TodoList v-if="currentPage === 2" />

    <button class="menu-button" name="0" v-if="currentPage > 0" @click="selectedMenu">back</button>

    <div class="footer">
      <p>copyright(c) 2020 lis</p>
    </div>
  </div>
</template>

<script>
import TickTackToe from "./components/TickTackToe";
import TodoList from "./components/TodoList";

export default {
  name: "App",
  components: {
    TodoList
  },
  data() {
    return {
      currentPage: 2,
    }
  },
  methods: {
    selectedMenu(event) {
      // alert(event.target.name);
      var nextPage = +event.target.name;
      this.currentPage = nextPage;
    }
  }
};
</script>

<style>
body,
body * {
  background-color: #222;
  color: #ccc;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
