<template>
  <main>
    <ul>
        <li class="text-center" v-for="(film, index) in list" :key="index">
            <div>Titolo: {{film.title}}</div>
            <div>Titolo originale: {{film.original_title}}</div>
            <div>Lingua: {{film.original_language}}</div>
            <div>Voto: {{film.vote_average}}</div>
        </li>
    </ul>
  </main>
</template>

<script>



export default {
name: "MainPage",
props: ['list'], 
}
</script>

<style lang="scss" scoped>
li {
  padding: 20px;
  
  list-style-type: none;
}
</style>




