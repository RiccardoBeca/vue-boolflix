<template>
  <div>
    <h1 class="title pt-5 mx-5">{{itemTitle}}</h1>
    <div class="container d-flex flex-wrap">
      <FilmCardComp :card="card" v-for="(card, index) in itemFilmArray" :key="`card${index}`"/>
      <TvCardComp :card="card" v-for="(card, index) in itemTvArray" :key="`card${index}`"/>
    </div>
    
  </div>
  
</template>

<script>
import FilmCardComp from './FilmCardComp.vue';
import TvCardComp from './TvCardComp.vue';


  export default {
    name: "MainComp",
    props: {
      itemFilmArray: Array,
      itemTvArray: Array,
      itemTitle: String
    },
    components: { 
      FilmCardComp,
      TvCardComp,
    }
  }
</script>

<style lang="scss" scoped>
@import '../assets/style/_vars.scss';
@import '../assets/style/_general.scss';
@import '../assets/style/_utils.scss';


.title{
  color: red
}
</style>



