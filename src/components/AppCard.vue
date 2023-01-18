<script>
export default {
    name: 'AppCard',
    props: {
        info: Object,
    },
    methods: {
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
    Flags(value) {
      let lang = '';
      if (value.original_language) {
        switch (value.original_language) {
          default:
            lang = (value.original_language)
            break;
          case 'en':
            lang = 'gb'
            break;
          case 'ja':
            lang = 'jp'
            break;
        }
        let urlFlag = lang.toUpperCase()
        return urlFlag
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

<div class="card" >
  <img class="card-img-top" :src="Image(info)" :alt="title(info)">
  <div class="card-body">
    <h5 class="card-title">{{ title(info) }}</h5>
    <p class="card-text">Titolo Originale: {{  originalTitle(info) }}</p>
    <p class="card-text">Voto:  
      <i v-for="star in stelle" class="fa-solid fa-star"></i>
      <i v-for="star in stelleVuote" class="fa-regular fa-star"></i>
    </p>
    <p class="card-text">Lingua: {{ info.original_language }}</p>
    <img :src="`https://www.countryflagicons.com/FLAT/64/${Flags(info)}.png`">
  </div>
</div>
</template>

<style lang="scss" scoped>

</style>