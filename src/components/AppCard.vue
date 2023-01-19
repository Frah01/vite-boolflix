<script>
export default {
    name: 'AppCard',
    props: {
        info: Object,
    },
    data(){
      return{
        hover : false
      }
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
   <div class="cards" @mouseenter="hover = true" @mouseleave="hover = false"><img class="copertina"  :src="Image(info)" :alt="title(info)"/>
    <div class="info" v-if="hover">
      <h5 class="card-title">{{ title(info) }}</h5>
      <p class="card-text">Titolo Originale: {{  originalTitle(info) }}</p>
    <p class="card-text">Voto:  
      <i v-for="star in stelle" class="fa-solid fa-star stars-color"></i>
      <i v-for="star in stelleVuote" class="fa-regular fa-star stars-empty-color"></i>
    </p>
    <p class="card-text d-flex">Lingua: {{ info.original_language.toUpperCase() }}
    
    </p>
    <!-- <img class="language"  :alt="`${info.original_language}`" :src="`https://unpkg.com/language-icons/icons/${info.original_language}.svg`"> -->
    <p class="card-text">Overview: {{ overview() }}</p>
    </div>
  </div>
<!-- <div class="card-container"  >
  <div class="card-body">
   
    
    
  </div>
</div> -->
</template>

<style lang="scss" scoped>

@use '../styles/general.scss' as*;
 .card-container{
  min-width: 300px;
  padding: 1px;
  position: relative;
  .card-body{
      padding: 20px;
      height: 100%;
      position: absolute;
      bottom: 0;
      left: 0;
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      color: white;
      background: linear-gradient(0deg, rgba(0,0,0,1) 0%, rgba(255,255,255,0) 100%);
    }
    
    .language{
      margin-left: 1em;
      width: 20px;
    }
    
  }
  .stars-color {
    color: orange;
  }

  .stars-empty-color {
    color: rgb(172, 172, 172);
  }

  .copertina  {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    -o-object-fit: cover;
     object-fit: cover;
      

  }

  .cards {
  margin-right: 10px;
  width: 305px;
  height: 500px;
  padding: 1.5rem;
  background: white;
  position: relative;
  display: flex;
  align-items: flex-end;
  transition: 0.4s ease-out;
  box-shadow: 0px 7px 10px rgba(0, 0, 0, 0.5);
}
.cards:hover {
  transform: translateY(-20px);
}
.cards:hover:before {
  opacity: 1;
}
.cards:hover .info {
  opacity: 1;
  transform: translateY(0px);
}
.cards:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  display: block;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.6);
  z-index: 2;
  transition: 0.5s;
  opacity: 0;
}
.cards .info {
  position: relative;
  z-index: 3;
  color: white;
  opacity: 0;
  transform: translateY(30px);
  transition: 0.5s;
}
.cards .info h1 {
  margin: 0px;
}
.cards .info p {
  letter-spacing: 1px;
  font-size: 15px;
  margin-top: 8px;
}

</style>