<template>
  <li class="list-group-item d-flex justify-content-between align-items-center">
    <div>{{ val }}</div>
    <div>
      <span class="me-3">{{ date }}</span>
      <button
        @click="emitComplete"
        :class="{
          'btn-success': completed ? true : false,
          'btn-danger': completed ? false : true,
        }"
        class="btn btn-sm me-2"
      >
        {{ completed ? "Done" : "Not yet" }}
      </button>
      <button class="btn btn-sm btn-danger" @click="emitDelete">X</button>
    </div>
  </li>
</template>

<script>
export default {
  props: ["val", "completed", "indeks", "date"],
  emits: ["checkComplete", "deleteTodo"],
  methods: {
    emitComplete() {
      this.$emit("checkComplete", this.indeks);
    },
    emitDelete() {
      this.$emit("deleteTodo", this.indeks);
    },
  },
};
</script>
