<template>
  <li>
    <label>
      <input type="checkbox" :checked="todo.done" @change="changeSelect" />
      <span v-show="!todo.isEdit">{{ todo.title }}</span>
      <input
        type="text"
        v-show="todo.isEdit"
        :value="todo.title"
        @keyup.enter="handleEnter(todo, $event)"
        @blur="handleEnter(todo, $event)"
        ref="inputTitle"
      />
    </label>
    <button class="btn btn-danger" @click="handleDelete">删除</button>
    <button
      v-show="!todo.isEdit"
      class="btn btn-edit"
      @click="handleEdit(todo)"
    >
      编辑
    </button>
  </li>
</template>

<script>
import pubsub from "pubsub-js";
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
        //  this.$bus.$emit("deleteTodo", this.todo.id);
        pubsub.publish("deleteTodo", this.todo.id);
      }
    },
    handleEdit(todo) {
      if (Object.prototype.hasOwnProperty.call(todo, "isEdit")) {
        todo.isEdit = true;
      } else {
        console.log("@@@");
        this.$set(todo, "isEdit", true);
      }
      this.$nextTick(function () {
        this.$refs.inputTitle.focus();
      });
    },
    handleEnter(todo, e) {
      todo.isEdit = false;
      if (!e.target.value.trim()) return alert("输入不能为空");
      this.$bus.$emit("updateTodo", todo.id, e.target.value);
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
