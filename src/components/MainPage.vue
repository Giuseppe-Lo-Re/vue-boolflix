<template>
  <main>

    <!-- Film -->
    <ul>
      <li 
        v-for="(film, index) in filmlist" 
        :key="index" 
        class="Film"
      >
        <div class="card">

          <!-- Cover Image -->
          <img class="cover" :src="getCoverImage(film.poster_path)" :alt="film.title">
          <div class="text">

            <!-- Title -->
            <div>
              <span>Titolo: </span> {{film.title}} 
            </div>

            <!-- Original Title -->
            <div>
              <span>Titolo originale: </span> {{film.original_title}} 
            </div>

            <!-- Language -->
            <div>
              <span>Lingua: </span> {{film.original_language}} 

              <!-- Flag -->
              <img class="flag" :src="getFlag(film.original_language)" :alt="film.original_language">
            </div>

            <!-- Vote Average -->
            <div>
              <span>Media Voto: </span>
              <span> <i v-for="n in trasformVote(film.vote_average)" :key="n" class="fa-solid fa-star star-space"></i></span>
            </div>

            <!-- Overview -->
            <div>
              <span>Overview: </span>
              <div class="overview">{{ film.overview }}</div>
            </div>
          </div>
        </div>
      </li>
    </ul>

    <!-- Series --> 
    <ul>
      <li 
        v-for="(serie, index) in serielist" 
        :key="index" 
        class="series"
      >
        <div class="card">

          <!-- Cover Image -->
          <img class="cover" :src="getCoverImage(serie.poster_path)" :alt="serie.name">
          <div class="text">

            <!-- Title -->
            <div>
              <span>Titolo:</span> {{serie.name}} 
            </div>

            <!-- Original Title -->
            <div>
              <span>Titolo originale:</span> {{serie.original_name}}
            </div>

            <!-- Language -->
            <div>
              <span>Lingua:</span> {{serie.original_language}}

              <!-- Flag -->
              <img class="flag" :src="getFlag(serie.original_language)" :alt="serie.original_language">
            </div>

            <!-- Vote Average -->
            <div>
              <span>Media Voto:</span>
              <span> <i v-for="n in trasformVote(serie.vote_average)" :key="n" class="fa-solid fa-star star-space"></i></span>
            </div>

            <!-- Overview -->
            <div>
              <span>Overview:</span>
              <div class="overview">{{ serie.overview }}</div>
            </div>
          </div>
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

// Sostituisce le bandiere mancanti
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
    } else if(Nationality == 'zh') {
      Nationality = "hk";
    }
  return `https://countryflagsapi.com/png/${Nationality}`;
},

// Scarica le immagini di copertina
getCoverImage(posterpath) {
  if(posterpath == null) {
    return `https://www.movienewz.com/wp-content/uploads/2014/07/poster-holder.jpg`;
  }
  return `https://image.tmdb.org/t/p/w342${posterpath}`;
},

// Trasforma il voto in stelle da 1 a 5
trasformVote(star) {
  const voteStars = star / 2;
  return Math.round(voteStars);
}
}
}

</script>

<style lang="scss" scoped>
@import "../style/common.scss";

main {
  color: black;

  ul {
    display: flex;
    flex-wrap: wrap;
    text-align: center;
    gap: 15px;
    justify-content: center;
    padding-top: 15px;

  }

  li {
  width: calc((100% / 5) - 20px);
  height: 100%;
  border: 1px solid red;

  

  .card {
    background-color: black;
    color: white;
    padding: 10px;
    cursor: pointer;
    height: 340px;
    box-shadow: 10px 10px 10px rgba(0, 0, 0, 0.5);
    overflow: auto;

    .cover {
    height: 320px;
    display: block;
    }
    .text {
      min-height: 320px;
      display: none;
    }

    &:hover .cover{
    display: none;
    }

    &:hover .text{
      display: block;
    }

    div {
      text-align: left;
      padding: 5px;

      span {
      font-weight: bold;
    }
    }

    .overview {
      font-style: italic;
      font-size: 14px;
           }
  }
  
  .flag {
    margin-left: 5px;
    border: 1px solid black;
    width: 20px;
    height: 14px;
  }

  span {
    i {
    color: yellow;
    }
  }
}
}
</style>




