<script setup>
import Movie from "./components/Movie.vue";
</script>

<template>
  <div class="app-container">
    <Suspense>
      <Movie />
    </Suspense>
  </div>
</template>

<style scoped>

</style>
