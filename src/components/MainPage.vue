<template>
  <main>
    <ul>
        <li class="text-center" v-for="(film, index) in filmList" :key="index">
            <div>Titolo: {{film.title}}</div>
            <div>Titolo originale: {{film.original_title}}</div>
            <div>Lingua: {{film.original_language}}</div>
            <div>Voto: {{film.vote_average}}</div>
        </li>
    </ul>
  </main>
</template>

<script>
// import axios from 'axios';


export default {
name: "MainPage",
props: ['searchtext'], 
data() {
    return {
      urlFilm:"https://api.themoviedb.org/3/search/movie?api_key=d950ce535bf05900292bb8ad7bb98628&language=en-US",
      filmList: [],
      textToSearch: []
    };
},
methods: {
  getArrayFromApi() {
    console.log(this.searchtext);
    // axios.get(`${this.urlFilm}&query=${this.searchtext}`)
    // .then((response) => {
    //   this.filmList = response.data.results;
    //   console.log(this.filmList);
    // });
  },

  }
}
</script>

<style lang="scss" scoped>
main {
  background-color:#424242;
}
</style>




