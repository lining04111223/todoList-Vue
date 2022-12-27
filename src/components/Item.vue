<template>
  <li>
    <label>
      <input type="checkbox" :checked="todo.done" @change="changeSelect" />
      <span>{{ todo.title }}</span>
    </label>
    <button class="btn btn-danger" style="display: none">删除</button>
  </li>
</template>

<script>
export default {
  name: `Item`,
  props: ["todo", "checkTodo"],
  methods: {
    changeSelect() {
      this.checkTodo(this.todo.id);
      console.log(this.todo.id);
    },
  },
};
</script>

<style scoped>
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}
</style>
