<template>
  <main>
    <div class="film">
      <ul>
          <li v-for="(film, index) in filmlist" :key="index">
              <div>Titolo: {{film.title}}</div>
              <div>Titolo originale: {{film.original_title}}</div>
              <div>Lingua: {{film.original_language}}</div>
              <div>Voto: {{film.vote_average}}</div>
          </li>
      </ul>
    </div>

  <div class="serie">
    <ul>
        <li v-for="(serie, index) in serielist" :key="index">
            <div>Titolo: {{serie.title}}</div>
            <div>Titolo originale: {{serie.original_title}}</div>
            <div>Lingua: {{serie.original_language}}</div>
            <div>Voto: {{serie.vote_average}}</div>
        </li>
    </ul>
  </div>
  </main>
</template>

<script>



export default {
name: "MainPage",
props: ['filmlist','serielist'] 
}
</script>

<style lang="scss" scoped>
main {
  display: flex;
}
li {
  padding: 20px;
  list-style-type: none;
}
</style>




