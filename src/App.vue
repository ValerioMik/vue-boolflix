<template>
  <div id="app">
    <header>
      <div id="logoapp">
        <h1>Booflix</h1>
      </div>
       <ImputUtente class="imput"/>
    </header>
    
    
  </div>
</template>

<script>
import ImputUtente from './components/ImputUtente.vue'


export default {
  name: 'App',
  components: {
   ImputUtente,
  }
}
</script>

<style lang="scss">
#app {
}
header{
  background-color: black;
   position: relative;
}
h1{
  color: red;
  font-size: 50px;
}
</style>
