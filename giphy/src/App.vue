<template>
  <div id="app">
    <search v-on:SearchRequested="handleSearch"></search>
    <p v-if="isLoading">Loading</p>
    <preview :gifs="gifs"></preview>
  </div>
</template>

<script>
import search from "./components/search.vue";
import preview from "./components/preview.vue";

export default {
  name: "app",
  components: {
    search,
    preview
  },
  data() {
    return {
      isLoading: true,
      gifs: []
    };
  },
  methods: {
    doQuery(url) {
      fetch(url)
        .then(res => {
          return res.json();
        })
        .then(res => {
          this.gifs = res.data;
          this.isLoading = false;
        });
    },
    handleSearch(query) {
      this.gifs = [];
      this.isLoading = true;
      const url =
        `https://api.giphy.com/v1/gifs/search?api_key=Elk1JqhpnrmJUtRnfWSK6Ci4Gk83BrWR&q=${encodeURI(query)}&limit=25&offset=0&rating=G&lang=en`;
      this.doQuery(url);
    }
  },

  created() {
    fetch(
      "https://api.giphy.com/v1/gifs/trending?api_key=Elk1JqhpnrmJUtRnfWSK6Ci4Gk83BrWR&limit=40&rating=G"
    )
      .then(res => {
        return res.json();
      })
      .then(res => {
        this.gifs = res.data;
        this.isLoading = false;
      });
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
