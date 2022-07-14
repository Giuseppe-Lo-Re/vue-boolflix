<template>
  <div id="app">

    <HeaderPage 
      @runSearch="SearchText"
    />
    
    <MainPage 
      :filmlist="filmList" 
      :serielist="serieList"
    />

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
      urlSerie:"https://api.themoviedb.org/3/search/tv?api_key=d950ce535bf05900292bb8ad7bb98628&language=en-US",
      filmList: [],
      seriesList:[]
    }
  },

  methods: {

  // Scarica i film attraverso l' API
  getFilmFromApi(userChoice) {
    axios.get(`${this.urlFilm}&query=${userChoice}`)
    .then((response) => {
      this.filmList = response.data.results;
    });
  },
  
  // Scarica le serie attraverso l' API
  getSeriesFromApi(userChoice) {
    axios.get(`${this.urlSerie}&query=${userChoice}`)
    .then((response) => {
      this.serieList = response.data.results;
    });
  },

  // Dopo la ricerca dell'utente fa partire le funzioni che scaricano i film e le serie
  SearchText(userChoice) {
    this.getFilmFromApi(userChoice);
    this.getSeriesFromApi(userChoice);
    }
  },
}
</script>

<style lang="scss" scoped>
@import "./style/common.scss";
</style>
