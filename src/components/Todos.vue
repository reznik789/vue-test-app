<template>
  <div>
    <h1>Todos</h1>
    <div v-for="todo in todos" :key="todo.id">
      <TodoItem :todo="todo" />
    </div>
  </div>
</template>
<script>
import TodoItem from "./TodoItem";
export default {
  name: "Todos",
  props: ["todos"],
  components: { TodoItem }
};
</script>
<style scoped></style>