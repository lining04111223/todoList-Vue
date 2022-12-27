<template>
  <div>
    <MyHeader :addTodo="addTodo" />
    <List :todos="todos" :checkTodo="checkTodo" :deleteTodo="deleteTodo" />
    <MyFooter :todos="todos" />
  </div>
</template>

<script>
import MyHeader from "./components/MyHeader.vue";
import MyFooter from "./components/MyFooter.vue";
import List from "./components/List.vue";
export default {
  name: "App",
  components: {
    MyHeader,
    List,
    MyFooter,
  },
  data() {
    return {
      todos: [
        { id: "001", title: "抽烟", done: true },
        { id: "002", title: "喝酒", done: false },
        { id: "003", title: "开车", done: true },
      ],
    };
  },
  methods: {
    addTodo(todo) {
      this.todos.unshift(todo);
    },
    checkTodo(id) {
      this.todos.forEach((todo) => {
        if (todo.id === id) {
          todo.done = !todo.done;
        }
      });
    },

    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
  },
};
</script>

<style></style>
