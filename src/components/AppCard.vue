<script>
export default {
    name: 'AppCard',
    props: {
        info: Object,
    },
    methods: {
      overview(){
      if (this.info.overview.length > 100){
        this.info.overview = this.info.overview.substring(0,100) + '...'
        return this.info.overview
      }
      return this.info.overview
    },
      title(value){
        if(value.media_type == 'tv'){
          return `Serie Tv: ${value.name}.`

        }
        else if(value.media_type == 'movie'){
          return `Film: ${value.title}.`
        }
        else{
          return `Title Undefined`
        }
      },
      originalTitle(value) {
      if (value.media_type == 'tv') {
        return value.original_name
      }
      else if (value.media_type == 'movie') {
        return value.original_title
      }
      else {
        return `Il titolo non è disponibile`
      }
    },
    Image(value) {
      if (value.poster_path) {
        return `https://image.tmdb.org/t/p/w300${value.poster_path}`
      }
      else {
        return `https://www.emugifs.net/wp-content/uploads/2021/07/Eh-Volevi-GIF-Zeb89-MEME-Reazione-Divertente-dello-YouTuber-Italiano-da-Usare-nei-Commenti-ai-Post-di-Facebook-o-nei-Gruppi-WhatsApp-Scarica-Gratis-e-Condividi.gif`
      }
    },
  },
    computed: {
    stelle() {
      let stelle = [];
      for (let i = 0; i < 5; i++) {
        if (i < Math.round(this.info.vote_average / 2)) {
          stelle.push(i);
        }
      }
      return stelle;
    },
    stelleVuote() {
      let stelleVuote = [];
      for (let i = 0; i < 5 -(Math.round(this.info.vote_average / 2)) ; i++) {
        stelleVuote.push(i)
      }
      return stelleVuote;
    },
   
  }
}
</script>

<template lang="">
<div class="card-container" >
  <img class="card-img" :src="Image(info)" :alt="title(info)">
  <div class="card-body">
    <h5 class="card-title">{{ title(info) }}</h5>
    <p class="card-text">Titolo Originale: {{  originalTitle(info) }}</p>
    <p class="card-text">Voto:  
      <i v-for="star in stelle" class="fa-solid fa-star stars-color"></i>
      <i v-for="star in stelleVuote" class="fa-regular fa-star stars-empty-color"></i>
    </p>
    <p class="card-text">Lingua: {{ info.original_language.toUpperCase() }}</p>
    <p class="card-text">Overview: {{ overview() }}</p>
    <img class="language"  :alt="`${info.original_language}`" :src="`https://unpkg.com/language-icons/icons/${info.original_language}.svg`">
  </div>
</div>
</template>

<style lang="scss" scoped>

@use '../styles/general.scss' as*;
 .card-container{
  padding: 1px;
  .card-body{
    padding: 20px;
    height: 100%;
    display: none;
  }
  .stars-color {
    color: orange;
  }

  .stars-empty-color {
    color: rgb(172, 172, 172);
  }

  .card-img {
    width: 100%;
  }

  &:hover{
    .card-body{
      display: block;
      background-color: rgba(0,0,0,);
      color: white;
    }
    img{
      display: none;
    }

    .language{
      display: block;
      width: 50px
    }
  }
 }
</style>