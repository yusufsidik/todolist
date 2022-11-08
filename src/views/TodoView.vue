<template>
  <div class="container">
    <h3 class="display-4 mt-3">Todo List</h3>
  </div>
  <div class="container d-flex align-items-center justify-content-center mt-4">
    <div class="card col-10 shadow">
      <div class="card-header bg-dark">
        <div class="d-flex gap-3 p-2 justify-content-between">
          <div class="form-group w-50">
            <input
              type="text"
              class="form-control"
              placeholder="Input Todo & Press Enter to add todo.."
              v-model.trim="input"
              @keyup.enter="submitTodo"
            />
          </div>
          <button
            class="btn btn-danger btn-sm rounded-pill px-3"
            @click="removeAll"
          >
            Delete All
          </button>
        </div>
      </div>
      <div class="card-body">
        <ul class="list-group">
          <span class="text-center" v-if="todos.length == 0">Empty Todo</span>
          <ListItem
            :val="todo.todo"
            :indeks="index"
            :date="todo.date"
            :completed="todo.isCompleted"
            @checkComplete="checkComplete"
            @deleteTodo="deleteTodo"
            v-for="(todo, index) in todos"
            :key="todo.id"
          />
        </ul>
      </div>
    </div>
  </div>
  <!-- <a target="_blank" href="https://icons8.com/icon/67884/delete">Delete</a>
icon by
<a target="_blank" href="https://icons8.com">Icons8</a> -->
</template>

<script>
import ListItem from "../components/todo/ListItem.vue";

export default {
  components: {
    ListItem,
  },
  data() {
    return {
      todos: [],
      input: "",
      date: new Date().toLocaleDateString(),
    };
  },
  watch: {
    // jika ada value baru atau update data baru maka data array baru akan di update ke localStorage todos
    todos: {
      handler(updateVal) {
        localStorage.setItem("todos", JSON.stringify(updateVal));
      },
      deep: true,
    },
  },
  methods: {
    submitTodo() {
      if (this.input == "") return;
      this.todos.unshift({
        id: this.randomNumber(),
        todo: this.input,
        date: this.date,
        isCompleted: false,
      });
      this.input = "";
    },
    randomNumber() {
      return Math.floor(Math.random() * (2000 - 10 + 1) + 10) * 3;
    },
    getTodos() {
      this.todos = JSON.parse(localStorage.getItem("todos"));
    },
    checkComplete(index) {
      this.todos[index].isCompleted = !this.todos[index].isCompleted;
    },
    deleteTodo(index) {
      return confirm("Delete this todo ?")
        ? this.todos.splice(index, 1)
        : false;
    },
    removeAll() {
      return this.todos.length == 0
        ? false
        : confirm("Delete All Todos ?")
        ? (this.todos = [])
        : false;
    },
  },
  computed: {
    filterTodoDone() {
      return this.todos.filter((todo) => {
        return todo.isCompleted == true;
      });
    },
    filterTodoNotDone() {
      return this.todos.filter((todo) => {
        return todo.isCompleted == false;
      });
    },
  },
  mounted() {
    this.getTodos();
  },
};
</script>
