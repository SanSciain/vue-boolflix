<template>
  <div id="app">
    <AppHeader @buttonClicked="searching($event)" />
    <AppMain :moviesList="moviesList" />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import axios from "axios";
import AppMain from "./components/AppMain.vue";
export default {
  name: "App",
  components: { AppHeader, AppMain },
  data() {
    return {
      moviesList: [],
    };
  },
  methods: {
    searching(searchKey) {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "15bbfb8536d9947b1429836f467bce3f",
            query: searchKey,
          },
        })
        .then((resp) => {
          resp.data.results.forEach((item) => {
            const movieObj = {
              title: item.title,
              ogTitle: item.original_title,
              language: item.original_language,
              score: parseInt(item.vote_average) / 2,
            };
            this.moviesList.push(movieObj);
          });
        });
    },
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
