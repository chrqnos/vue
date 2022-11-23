<script setup>
import { ref } from "vue";
import axios from "axios";

const id = ref("");
const movie = ref(null);

const getMovies = async () => {
  const data = id.value;
  movie.value = (
    await axios.get("https://api.themoviedb.org/3/search/movie", {
      params: {
        api_key: "0a4dbc5e3b74420548bdd09d59591acf",
        query: data,
      },
    })
  ).data;
};
</script>

<template>
  <select v-model="id">
    <option value="293660">Deadpool</option>
  </select>
  <button @click="getMovies">Get</button>
  <div v-if="movie" class="movie-container">
    <p>Overview: {{movie.overview}}</p>
  </div>
</template>

<style scoped>

</style>
