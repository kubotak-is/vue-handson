<template>
  <div id="app">
    <button @click="deleteTodo">選択したTODOを削除</button>
    <ul>
      <li v-for="todo in todos">
        <input type="checkbox" v-model="todo.checked"> {{ todo.title }}
      </li>
    </ul>

    <div>
      <input
        type="text"
        v-model="value"
        @keyup.enter="add"
        placeholder="add todo">
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      todos: [],
      value: '',
    }
  },
  methods: {
    add() {
      this.todos.push({
        title: this.value,
        checked: false
      });
      console.log(this.todos);
      this.value = ""; // reset
    },
    deleteTodo() {
      this.todos = this.todos.filter(todo => {
        if (!todo.checked) return true;
      });
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
