<template>
  <div id="imput">
    <input type="text" placeholder="Inserisci un film" v-model.trim="imputText">
    <button @click.prevent="testotrovato">CERCA</button>
    <CardFilm v-for="films,i in filtralalistapersonaggi"
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
      apiUrl:"https://api.themoviedb.org/3/search/movie?api_key=c766fe019c512e0736766f4ff20690b2&query="+this.ricercatext,
       listadeiFilm:[],
       imputText:"",
       ricercatext:""
    }
  },
  created(){
   this.informazioniFilm();
  },
  computed:{
    filtralalistapersonaggi(){
      if(this.ricercatext === ""){
        return this.listadeiFilm
      }
      return this.listadeiFilm.filter((item)=>{
        return item.title.toLowerCase().icludes(this.ricercatext.toLowerCase())
      })
    }
  },
  methods:{
    informazioniFilm(){
      axios
      .get(this.apiUrl)
      .then((result)=>{
        this.listadeiFilm = result.data.results
       console.log(result.data.results);
      })
    },
    testotrovato(){
      this.ricercatext = this.imputText;
      console.log(this.ricercatext);
    }
  }
}
</script>

<style lang="scss">

</style>
