<template>
  <li>
    <label>
      <input type="checkbox" :checked="todo.done" @change="changeSelect" />
      <span>{{ todo.title }}</span>
    </label>
    <button class="btn btn-danger" @click="handleDelete">删除</button>
  </li>
</template>

<script>
export default {
  name: `Item`,
  props: ["todo"],
  methods: {
    changeSelect() {
      //this.checkTodo(this.todo.id);
      this.$bus.$emit("checkTodo", this.todo.id);
    },
    handleDelete() {
      console.log(this.todo.id);
      if (confirm("确定吗？")) {
        //this.deleteTodo(this.todo.id);
        this.$bus.$emit("deleteTodo", this.todo.id);
      }
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

li button {
  float: right;
  display: none;
  margin-top: 3px;
}
li:hover {
  background-color: #ddd;
}

li:hover button {
  display: block;
}
</style>
