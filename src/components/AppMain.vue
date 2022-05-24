<template>
  <main>
    <div class="container movies">
      <MovieCard
        v-for="(movieItem, index) in moviesList"
        :key="index"
        :movie="movieItem"
      />
    </div>
  </main>
</template>

<script>
import MovieCard from "./MovieCard.vue";
export default {
  name: "AppMain",
  props: {
    moviesList: Array,
  },
  components: { MovieCard },
};
</script>

<style lang="scss" scoped>
.movies {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
