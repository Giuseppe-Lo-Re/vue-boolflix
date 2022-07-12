<template>
  <main>

  </main>
</template>

<script>
import axios from 'axios';


export default {
name: "MainPage",

data() {
    return {
      urlFilm:"https://api.themoviedb.org/3/search/movie?api_key=d950ce535bf05900292bb8ad7bb98628&language=en-US",
      filmList: []
    };
},
methods: {
  getArrayFromApi(query) {
    axios.get(`${this.urlFilm}&query=${query}`)
    .then((response) => {
      const arrayFilm = response.data.results;
    });
  }
}
}
</script>

<style lang="scss" scoped>
main {
  background-color:#424242;
}
</style>




