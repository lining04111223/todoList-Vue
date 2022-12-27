<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" />
    </label>

    <span>
      <span>已完成{{ doneCheck }}</span
      >/全部{{ todos.length }}</span
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
  props: ["todos"],
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
  },
};
</script>

<style scoped></style>
