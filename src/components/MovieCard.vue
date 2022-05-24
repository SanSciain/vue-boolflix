<template>
  <div class="card">
    <h3>{{ movie.title }}</h3>
    <h4>{{ movie.ogTitle }}</h4>
    <div class="flag-icon-container">
      <img
        :src="`https://www.countryflagicons.com/FLAT/64/${movie.language.toUpperCase()}.png`"
        @error="languageNotFound"
        v-if="flag"
        :alt="movie.language"
      />
      <p v-else>Lang Flag 404</p>
    </div>
    <p>{{ movie.score }}</p>
  </div>
</template>

<script>
export default {
  name: "MovieCard",
  data() {
    return {
      flag: true,
    };
  },
  props: {
    movie: Object,
  },
  methods: {
    languageNotFound() {
      this.flag = false;
    },
  },
};
</script>

<style lang="scss" scoped>
.card {
  width: 150px;
  border: 1px solid black;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 2rem;
  padding: 1rem;
  flex-grow: 1;

  .flag-icon-container {
    width: 30px;

    p {
      font-size: 0.6rem;
    }
  }
}
</style>
