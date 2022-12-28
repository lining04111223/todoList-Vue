<template>
  <ul class="todo-main">
    <transition-group
      appear
      name="animate__animated animate__bounce"
      enter-active-class="animate__bounceInRight"
      leave-active-class="animate__fadeOutRight"
    >
      <Item v-for="todoOBJ in todos" :key="todoOBJ.id" :todo="todoOBJ" />
    </transition-group>
  </ul>
</template>

<script>
import Item from "./Item.vue";
import "animate.css";
export default {
  name: `List`,

  components: {
    Item,
  },
  props: ["todos"],
};
</script>

<style scoped>
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>
