<template>
  <div class="my-5">
    <img src="" alt="copertina">
    <h1>{{card.name}}</h1>
    <h2 v-if="card.original_name === card.name">{{card.name}}</h2>
    <h2 v-else>{{card.original_name}}</h2>
    <h3>{{card.original_language}}</h3>
    <h3 v-if="card.original_language == 'en'">
      <span>Lingua originale: </span>
      <img class="flags" src="../assets/img/Flag_of_the_United_Kingdom.svg.png" alt="">
    </h3>
    <h3 v-else-if="card.original_language == 'it'">
      <span>Lingua originale: </span>
      <img class="flags" src="../assets/img/index.png" alt="">
    </h3>
    <h3 v-else>Language:{{card.original_language}}</h3>
    <h4>{{card.vote_average}}</h4>
    <hr>

    <!-- modifica e aggiungi flags -->
  </div>
</template>

<script>
export default {
  name: "TvCardComp",
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