<template>
  <div id="app">

    <HeaderPage @runSearch="SearchText"/>
    
    <MainPage :list="filmList"/>

  </div>
</template>

<script>
import HeaderPage from "./components/HeaderPage";
import  MainPage  from "./components/MainPage";
import axios from 'axios';

export default {
  name: 'App',
  components: {
    HeaderPage,
    MainPage
  
  },
  data() {
    return {
      urlFilm:"https://api.themoviedb.org/3/search/movie?api_key=d950ce535bf05900292bb8ad7bb98628&language=en-US",
      filmList: []
    }
  },
  methods: {
  getArrayFromApi(userChoice) {
    console.log(userChoice);
    axios.get(`${this.urlFilm}&query=${userChoice}`)
    .then((response) => {
      this.filmList = response.data.results;
      console.log(this.filmList);
    });
  },
  SearchText(userChoice) {
    this.getArrayFromApi(userChoice)
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
