<template>
  <main>
    <div class="container movies">
      <MovieCard
        v-for="(movieItem, index) in moviesList"
        :key="index"
        :item="movieItem"
        :stat="status[0]"
        :type="'movie'"
      />
    </div>
    <div class="container movies">
      <MovieCard
        v-for="(seriesItem, index) in seriesList"
        :key="index"
        :item="seriesItem"
        :stat="status[1]"
        :type="'tv'"
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
    seriesList: Array,
    status: Array,
  },
  components: { MovieCard },
};
</script>

<style lang="scss" scoped>
main {
  background-color: grey;
  min-height: calc(100vh - 100px);

  .movies {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
}
</style>
