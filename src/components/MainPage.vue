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
          <img 
            :src="getCoverImage(film.poster_path)" 
            :alt="film.title" 
            class="cover"
          >
          <div class="text">

            <!-- Title -->
            <div>
              <span>
                Titolo: </span> {{ film.title }} 
            </div>

            <!-- Original Title -->
            <div>
              <span>Titolo originale: </span> {{ film.original_title }} 
            </div>

            <!-- Language -->
            <div>
              <span>Lingua: </span> {{ film.original_language }} 

              <!-- Flag -->
              <img 
                :src="getFlag(film.original_language)" 
                :alt="film.original_language"
                class="flag"
              >
            </div>

            <!-- Vote Average -->
            <div>
              <span>Media Voto: </span>

              <!-- Full Stars -->
              <span>
                <i 
                  v-for="n in trasformVote(film.vote_average)" 
                  :key="n" 
                  class="fa-solid fa-star star-space"
                >
                </i>

                <!-- Empty Stars -->
                <i 
                  v-for="n in 5 - trasformVote(film.vote_average)" 
                  :key="n" 
                  class="far fa-star"
                >
                </i>
                </span>
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
        v-for="(series, index) in serieslist" 
        :key="index" 
        class="series"
      >
        <div class="card">

          <!-- Cover Image -->
          <img 
            :src="getCoverImage(series.poster_path)" 
            :alt="series.name"
            class="cover" 
          >
          <div class="text">

            <!-- Title -->
            <div>
              <span>Titolo: </span> {{ series.name }} 
            </div>

            <!-- Original Title -->
            <div>
              <span>Titolo originale: </span> {{ series.original_name }}
            </div>

            <!-- Language -->
            <div>
              <span>Lingua: </span> {{ series.original_language }}

              <!-- Flag -->
              <img 
                :src="getFlag(series.original_language)" 
                :alt="series.original_language"
                class="flag"
              >
            </div>

            <!-- Vote Average -->
            <div>
              <span>Media Voto: </span>
              <span>
                <i 
                  v-for="n in trasformVote(series.vote_average)" 
                  :key="n" 
                  class="fas fa-star"
                >
                </i>
                <i 
                  v-for="n in 5 - trasformVote(series.vote_average)" 
                  :key="n" 
                  class="far fa-star"
                >
                </i>
              </span>
            </div>

            <!-- Overview -->
            <div>
              <span>Overview: </span>
              <div class="overview">{{ series.overview }}</div>
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
props: ['filmlist','serieslist'] ,
methods : {

// Sostituisce le bandiere mancanti:
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
    } else if(Nationality == 'da') {
      Nationality = "dk";
    }
  return `https://countryflagsapi.com/png/${Nationality}`;
},

// Scarica le immagini di copertina:
getCoverImage(posterpath) {
  if(posterpath == null) {
    return `https://www.movienewz.com/wp-content/uploads/2014/07/poster-holder.jpg`;
  }
  return `https://image.tmdb.org/t/p/w342${posterpath}`;
},

// Trasforma il voto in stelle da 1 a 5:
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

    li {
      width: calc((100% / 5) - 20px);
      height: 100%;
      border: 3px solid red;

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

    &:hover .cover {
      display: none;
    }

    &:hover .text {
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
}
}
</style>




