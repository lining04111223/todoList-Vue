<template>
  <div class="todo-footer" v-show="total">
    <label>
      <!--<input :checked="ifEaqual" type="checkbox" @click="selectAll" />-->
      <!--//v-model 实现初始化与绑定，good！！！-->
      <input v-model="ifEaqual" type="checkbox" />
    </label>

    <span>
      <span>已完成{{ doneCheck }}</span
      >/全部{{ total }}</span
    >
    <button class="btn btn-danger" @click="clearAll">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: `MyFooter`,
  data() {
    return { name: "lighthouse", address: "Vancouver" };
  },
  props: ["todos", "selectAllTodo", "clearAllTodo"],
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
    ifEaqual: {
      get() {
        return this.doneCheck === this.total && this.total !== 0;
      },
      set(value) {
        this.selectAllTodo(value);
      },
    },
  },
  methods: {
    clearAll() {
      if (confirm("确定吗？")) {
        this.clearAllTodo();
      }
    },
  },
};
</script>

<style scoped></style>
