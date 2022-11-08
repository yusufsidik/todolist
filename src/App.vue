<template>
  <TheNavbar />
  <small class="position-absolute bottom-0 start-50 mb-2"
    >&copy;kholid yusuf sidik</small
  >
</template>

<script>
import TheNavbar from "./components/TheNavbar.vue";
const url = `https://imdb-api.com/en/API/`;
const API_KEY = `k_gss5a58q`;
export default {
  components: {
    TheNavbar,
  },
  provide() {
    return {
      URL: url,
      API_KEY: API_KEY,
    };
  },
};
</script>
