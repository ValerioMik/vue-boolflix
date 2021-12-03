<template>
  <div>
    <div id="dettagli">
      <h2>Film</h2>
      <h2>Titolo: {{ details.title }}</h2>
      <h3>Titolo Originale: {{ details.original_title }}</h3>
      <span><img :src="bandieraImmagini()" /></span>
      <br />
      Voto:<star-rating :rating="votoArrotondato()" v-bind:star-size="30">
      </star-rating>
    </div>
    <div id="immagini">
      <img :src="importaImmagini()" :alt="details.original_title" />
    </div>
  </div>
</template>


<script>
import StarRating from "vue-star-rating";

export default {
  name: "CardFilm",
  components: {
    StarRating,
  },
  props: {
    details: Object,
  },
  methods: {
    bandieraImmagini() {
      if (this.details.original_language === "it") {
        return "https://www.buy-spares.ie/sites/responsive/img/universal/flags/it-flag.png";
      } else if (this.details.original_language === "en") {
        return "https://th.bing.com/th/id/R.8a8a985a6266b52f32e326ef17603955?rik=uoYiPLaWj9Yt0g&riu=http%3a%2f%2fwww.rgledhill.co.uk%2fimages%2fgb_flag.gif&ehk=IYDSLs30Co0xTYL1Zh9%2bhzwBPjI3S2IfGi5SQdjVkro%3d&risl=&pid=ImgRaw&r=0";
      } else if (this.details.original_language === "es") {
        return "https://th.bing.com/th/id/R.c5d09f69c2b8c99438e176963abbdecb?rik=VMtAUlZ9%2bXaBvg&riu=http%3a%2f%2fwww.dsalenia.it%2fimages%2fflag_spanish.gif&ehk=5Ezc4PsSThB1njE2MDMbZIwCKiIDKn4YwL0Xo7EJNZc%3d&risl=&pid=ImgRaw&r=0";
      } else {
        return "not-found";
      }
    },
    importaImmagini() {
      if (this.details.detposter_path !== null) {
        return `https://image.tmdb.org/t/p/w342${this.details.poster_path}`;
      }
      console.log("niente");
      return `https://www.losbagliato.it/wp-content/uploads/2021/07/copertina-netflix-23-giugno-960x960.png`;
    },
    votoArrotondato() {
      return this.details.vote_average / 2;
    },
  },
};
</script>

<style lang="scss">
a:hover >#dettagli {
  border: 2px solid rgb(255, 255, 255);
  background-color: black;
  cursor: pointer;
  width: 100%;
  display: block;
  margin: 20px;
}
#dettagli {
  display: none;
}
h2,h3{
  color: white;
}
#immagini{
  margin: 20px;
  border: 2px solid rgb(255, 255, 255);
 
}


</style>
