<template>
  <div id="dettagli">
    <h2>Film</h2>
    <h2>{{ details.title }}</h2>
    <h3>{{ details.original_title }}</h3>
    <span><img :src="bandieraImmagini()"/></span>
    <br />
    <star-rating :rating="votoArrotondato()" 
    star-size="30" 
    increment="0.5" 
    :show-rating="false">
    </star-rating>
    <img :src="importaImmagini()" :alt="details.original_title">
  </div>
</template>


<script>
import StarRating from 'vue-star-rating'


export default {
  name: 'CardFilm',
  components: {
   StarRating,
  },
  props: {
      details:Object,
  },
  methods:{
    bandieraImmagini(){
        if(this.details.original_language === 'it'){
          return "https://www.buy-spares.ie/sites/responsive/img/universal/flags/it-flag.png"
        }else if(this.details.original_language === 'en'){
          return "https://th.bing.com/th/id/R.8a8a985a6266b52f32e326ef17603955?rik=uoYiPLaWj9Yt0g&riu=http%3a%2f%2fwww.rgledhill.co.uk%2fimages%2fgb_flag.gif&ehk=IYDSLs30Co0xTYL1Zh9%2bhzwBPjI3S2IfGi5SQdjVkro%3d&risl=&pid=ImgRaw&r=0"
        }else if(this.details.original_language === 'es'){
          return "https://th.bing.com/th/id/R.c5d09f69c2b8c99438e176963abbdecb?rik=VMtAUlZ9%2bXaBvg&riu=http%3a%2f%2fwww.dsalenia.it%2fimages%2fflag_spanish.gif&ehk=5Ezc4PsSThB1njE2MDMbZIwCKiIDKn4YwL0Xo7EJNZc%3d&risl=&pid=ImgRaw&r=0"
        }else {
          return "not-found"
        }
    },
    importaImmagini(){
      if(this.details.detposter_path !== null){
        return `https://image.tmdb.org/t/p/w342${this.details.poster_path}`
      }else if (this.details.poster_path === null){
        return `https://www.bing.com/images/search?view=detailV2&ccid=u2ER7yAH&id=B05C1C33B4AB44FAC4EF34E3A1536A7100D3866B&thid=OIP.u2ER7yAH5KVceF5d9Z8rKAAAAA&mediaurl=https%3a%2f%2fdarienite.com%2fwp-content%2fuploads%2f2016%2f12%2fScreen-Shot-2016-12-26-at-11.20.00-AM-336x336.png&cdnurl=https%3a%2f%2fth.bing.com%2fth%2fid%2fR.bb6111ef2007e4a55c785e5df59f2b28%3frik%3da4bTAHFqU6HjNA%26pid%3dImgRaw%26r%3d0&exph=336&expw=336&q=+netflix+logo+w342+&simid=608034981228797524&FORM=IRPRST&ck=82C9B240B3FCE8A1CBEE65DE5CA831B2&selectedIndex=7`
      }
    },
    votoArrotondato(){
       return (this.details.vote_average / 2)
    }
  },
 
}
</script>

<style lang="scss">
#dettagli{
  
}
</style>
