<template>
  <div class="my-5">
    <h1>{{card.title}}</h1>
    <h2>{{card.original_title}}</h2>
    <h3 v-if="card.original_language == 'en'">
      <img src="../assets/img/Flag_of_the_United_Kingdom.svg.png" alt="">
    </h3>
     <h3 v-else-if="card.original_language == 'it'">
      <img src="../assets/img/index.png" alt="">
    </h3>
    <h3 v-else>Language:{{card.original_language}}</h3>
    <h4>{{card.vote_average}}</h4>
    <hr>
  </div>
</template>

<script>
export default {
  name: "FilmCardComp",
  props:{
    card:Object,
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/_vars.scss';
@import '../assets/style/_general.scss';
@import '../assets/style/_utils.scss';

</style>