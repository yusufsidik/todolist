<template>
  <div class="card-header" v-if="todos.length > 0">
    <div class="card-title">Todo Done</div>
  </div>
  <div class="card-body" v-if="todos.length > 0">
    <ul class="list-group">
      <span class="text-center" v-if="todos.length == 0">Empty Todo</span>
      <ListItem
        :val="todo.todo"
        :indeks="index"
        :completed="todo.isCompleted"
        @checkComplete="checkComplete"
        @deleteTodo="deleteTodo"
        v-for="(todo, index) in todos"
        :key="todo.id + '-Done'"
      />
    </ul>
  </div>
</template>

<script>
import ListItem from "./ListItem.vue";
export default {
  components: {
    ListItem,
  },
  props: ["todos"],
};
</script>
