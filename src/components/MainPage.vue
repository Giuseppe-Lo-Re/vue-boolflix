<template>
  <main>

  </main>
</template>

<script>
import axios from 'axios';


export default {
name: "MainPage",
props: ['text'],
data() {
    return {
      urlFilm:"https://api.themoviedb.org/3/search/movie?api_key=d950ce535bf05900292bb8ad7bb98628&language=en-US",
      filmList: [],
      textToSearch: []
    };
},
methods: {
  getArrayFromApi(query) {
    axios.get(`${this.urlFilm}&query=${query}`)
    .then((response) => {
      const filmList = response.data.results;
    });
  },
  SearchText(text) {
      this.textToSearch = text;
    }
  }
}
</script>

<style lang="scss" scoped>
main {
  background-color:#424242;
}
</style>




