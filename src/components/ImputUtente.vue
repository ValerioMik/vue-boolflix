<template>
  <div id="imput">
    <input
      type="text"
      placeholder="Inserisci un film"
      v-model.trim="imputText"
    />
    <button @click.prevent="testotrovato">CERCA</button>
    <CardFilm v-for="(films, i) in listadeiFilm" :key="'moovie'+i" :details="films" />
    <CardSerie v-for="(serie, i) in listadeiSerie" :key="'serie'+i" :details="serie"/>
  </div>
</template>

<script>
import axios from 'axios';
import CardFilm from '@/components/CardFilm.vue'
import CardSerie from '@/components/CardSerie.vue'

export default {
  name: 'ImputUtente',
  components: {
    CardFilm,
    CardSerie
  },
  data(){
    return{
      apiUrl:"https://api.themoviedb.org/3/search/movie?api_key=c766fe019c512e0736766f4ff20690b2&query=",
      apiUrlSerie:"https://api.themoviedb.org/3/search/tv?api_key=c766fe019c512e0736766f4ff20690b2&language=it_IT&query=",
      listadeiFilm: [],
      listadeiSerie:[],
      imputText: "spiderman",
    }
  },
  created(){
    this.informazioniFilm();
    this.informazioniSerie();
  },
  methods:{
    informazioniFilm(){
      axios
      .get(this.apiUrl+this.imputText)
      .then((result)=>{
        this.listadeiFilm = result.data.results
        console.log(result.data.results);
      })
    },
    informazioniSerie(){
      axios
      .get(this.apiUrlSerie+this.imputText)
      .then((result)=>{
        this.listadeiSerie = result.data.results
        console.log(result.data.results);
      })
    },
    testotrovato(){
      this.informazioniFilm();
      this.informazioniSerie();
    },
  }
}
</script>

<style lang="scss">
</style>
