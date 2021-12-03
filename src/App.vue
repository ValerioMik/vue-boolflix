<template>
  <div id="app">
    <ImputUtente/>
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
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
