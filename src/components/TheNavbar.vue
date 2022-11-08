<!-- eslint-disable vue/no-parsing-error -->
<template>
  <nav class="navbar navbar-expand-lg bg-light p-0">
    <div class="container py-2">
      <RouterLink to="/" class="navbar-brand">
        <img src="/src/assets/img/app.png" alt="" width="35" />
      </RouterLink>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <RouterLink
              to="/todo"
              class="nav-link"
              :class="{ active: nameRoute() == 'todo' ? true : false }"
              >Todo</RouterLink
            >
          </li>
          <li class="nav-item">
            <RouterLink
              to="/about"
              class="nav-link"
              :class="{ active: nameRoute() == 'about' ? true : false }"
              >About</RouterLink
            >
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <RouterView />
</template>

<script>
import { RouterLink, RouterView } from "vue-router";

export default {
  components: {
    RouterLink,
    RouterView,
  },
  data() {
    return {
      nav: "",
    };
  },
  methods: {
    nameRoute() {
      return this.$route.name;
    },
  },
};
</script>

<style scoped>
.active {
  position: relative;
}
.active::after {
  content: "";
  position: absolute;
  display: block;
  width: 80%;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  border: 1.5px solid orange;
}
</style>
