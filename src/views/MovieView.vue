<template>
  <div class="container d-flex justify-content-center align-items-center">
    <div class="col-12">
      <h5 class="display-4">Box Office Movie</h5>
      <hr class="w-50" />
      <div class="d-flex justify-content-center flex-row flex-wrap gap-3">
        <TheList
          v-for="movie in movies"
          :title="movie.title"
          :image="movie.image"
          :id="movie.id"
          :key="movie.id"
          :rank="movie.rank"
        />
      </div>
    </div>
  </div>
</template>

<script>
import TheList from "../components/movie/TheLIst.vue";

export default {
  inject: ["URL", "API_KEY"],
  components: {
    TheList,
  },
  data() {
    return {
      endpoint: "BoxOffice",
      movies: [],
    };
  },
  methods: {
    async getMovie() {
      return await fetch(`${this.URL}${this.endpoint}/${this.API_KEY}`, {
        method: "GET",
        headers: {
          "Content-Type": "appplication/json",
        },
      })
        .then((data) => {
          return data.json();
        })
        .then((result) => {
          this.movies = result.items;
        });
    },
  },
  created() {
    this.getMovie();
  },
};
</script>
