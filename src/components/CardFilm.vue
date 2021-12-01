<template>
  <div id="dettagli">
    <h2>{{details.title}}</h2>
    <h3>{{details.original_title}}</h3>
    <span>{{details.original_language}}</span><br>
    <span>{{details.vote_average}}</span>
  </div>
</template>


<script>


export default {
  name: 'CardFilm',
  props: {
      details:Object,
  }
}
</script>

<style lang="scss">

</style>
