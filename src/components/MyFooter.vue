<template>
  <div class="todo-footer" v-show="total">
    <label>
      <input :checked="ifEaqual" type="checkbox" @click="selectAll" />
    </label>

    <span>
      <span>已完成{{ doneCheck }}</span
      >/全部{{ total }}</span
    >
    <button class="btn btn-danger">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: `MyFooter`,
  data() {
    return { name: "lighthouse", address: "Vancouver" };
  },
  props: ["todos", "selectAllTodo"],
  computed: {
    doneCheck() {
      let i = 0;
      this.todos.forEach((todo) => {
        if (todo.done) {
          i++;
        }
      });
      return i;
    },
    total() {
      return this.todos.length;
    },
    ifEaqual() {
      return this.doneCheck === this.total && this.total !== 0;
    },
  },
  methods: {
    selectAll(e) {
      console.log(e.target.checked);
      this.selectAllTodo(e.target.checked);
    },
  },
};
</script>

<style scoped></style>
