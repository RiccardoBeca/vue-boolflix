<template>
  <div class="p-5 my-5">
    <img class="copertina" :src="`https://image.tmdb.org/t/p/w342${card.poster_path}`" alt="copertina">
    <h1>{{card.title}}</h1>
    <h2>{{card.original_title}}</h2>
    <h3 v-if="card.original_language == 'en'">
      <span>Lingua originale: </span>
      <img class="flags" src="../assets/img/Flag_of_the_United_Kingdom.svg.png" alt="">
    </h3>
     <h3 v-else-if="card.original_language == 'it'">
      <span>Lingua originale: </span>
      <img class="flags" src="../assets/img/index.png" alt="">
    </h3>
    <h3 v-else>Language:{{card.original_language}}</h3>
    <span v-for="stellina in arrotondaVoto()" :key="stellina">
      &starf;
    </span>
    <span v-for="stellinaVuota in 5 - arrotondaVoto()" :key="stellinaVuota">
      &star;
    </span>
    <hr>
  </div>
</template>

<script>
export default {
  name: "FilmCardComp",
  props:{
    card:Object,
  },
  methods: {
    arrotondaVoto(){
     return Math.round(this.card.vote_average / 2);
    }
  },
}
</script>

<style lang="scss" scoped>
@import '../assets/style/_vars.scss';
@import '../assets/style/_general.scss';
@import '../assets/style/_utils.scss';

.flags{
  width: 50px;
}

</style>