<template>
  <main>

    <!-- Film -->
    <ul>
        <li v-for="(film, index) in filmlist" :key="index">
            <div>
              Titolo: {{film.title}} 
            </div>
            <div>
              Titolo originale: {{film.original_title}} 
            </div>
            <div>
              Lingua: {{film.original_language}} 

              <!-- Flag -->
              <img :src="getFlag(film.original_language)" :alt="film.original_language">
            </div>
            <div>
              Voto: {{film.vote_average}}
            </div>
        </li>
    </ul>

    <!-- Series -->
    <ul>
        <li v-for="(serie, index) in serielist" :key="index">
          <div>
            Titolo: {{serie.name}} 
          </div>
          <div>
            Titolo originale: {{serie.original_name}}
          </div>
          <div>
            Lingua: {{serie.original_language}}

            <!-- Flag -->
            <img :src="getFlag(serie.original_language)" :alt="serie.original_language">
          </div>
          <div>
            Voto: {{serie.vote_average}} 
          </div>
        </li>
    </ul>
  </main>
</template>

<script>
export default {
name: "MainPage",
props: ['filmlist','serielist'] ,
methods : {

  getFlag(Nationality) {
    if(Nationality == 'en') {
        Nationality = "gb";
      } else if(Nationality == 'ja') {
        Nationality = "jp";
      } else if(Nationality == 'hi') {
        Nationality = "in";
      } else if(Nationality == 'cs') {
        Nationality = "cz";
      } else if(Nationality == 'ko') {
        Nationality = "kr";
      } else if(Nationality == 'sv') {
        Nationality = "ch";
      }
    return `https://countryflagsapi.com/png/${Nationality}`;
  }
}
}


</script>

<style lang="scss" scoped>
@import "../style/common.scss";
main {
  color: white;
  li {
  padding: 20px;
  list-style-type: none;

  img {
    margin-left: 5px;
    border: 1px solid black;
    width: 20px;
    height: 12px;
  }
}
}
</style>




