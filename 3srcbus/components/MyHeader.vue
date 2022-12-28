<template>
  <div class="todo-header">
    <input type="text" placeholder="请输入任务名称" @keyup.enter="add" />
  </div>
</template>

<script>
import { nanoid } from "nanoid";
export default {
  name: `MyHeader`,
  methods: {
    add(e) {
      const todoOBJ = {
        id: nanoid(),
        title: e.target.value,
        done: false,
      };
      this.$emit("addTodo", todoOBJ);
      e.target.value = "";
    },
  },
};
</script>

<style scoped>
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
}

.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075),
    0 0 8px rgba(82, 168, 236, 0.8);
}
</style>
