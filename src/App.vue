<template>
  <div id="app">
    <AppHeader @buttonClicked="searching($event)" />
    <AppMain
      :moviesList="moviesList"
      :seriesList="seriesList"
      :status="status"
    />
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
      seriesList: [],
      status: [],
    };
  },
  methods: {
    searching(searchKey) {
      const options = {
        params: {
          api_key: "15bbfb8536d9947b1429836f467bce3f",
          query: searchKey,
        },
      };
      const reqMovies = axios.get(
        "https://api.themoviedb.org/3/search/movie",
        options
      );
      const reqSeries = axios.get(
        "https://api.themoviedb.org/3/search/tv",
        options
      );
      axios.all([reqMovies, reqSeries]).then((resp) => {
        this.moviesList = resp[0].data.results;
        this.seriesList = resp[1].data.results;
        this.status.push(resp[0].status);
        this.status.push(resp[1].status);
      });
    },
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
