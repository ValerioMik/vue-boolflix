<template>
  <div id="imput">
    <input type="text" placeholder="Inserisci un film">
    <button>CERCA</button>
    <CardFilm v-for="films,i in listadeiFilm"
    :key="i"
    :details="films"/>
  </div>
</template>

<script>
import axios from 'axios';
import CardFilm from '@/components/CardFilm.vue'

export default {
  name: 'ImputUtente',
  components: {
    CardFilm,
  },
  data(){
    return{
      apiUrl:"https://api.themoviedb.org/3/search/movie?api_key=c766fe019c512e0736766f4ff20690b2&query=Spider+man",
       listadeiFilm:[],
    }
  },
  created(){
   this.informazioniFilm();
  },
  methods:{
    informazioniFilm(){
      axios
      .get(this.apiUrl)
      .then((result)=>{
        this.listadeiFilm = result.data.results
       console.log(result.data.results);
      })
    }
  }
}
</script>

<style lang="scss">

</style>
