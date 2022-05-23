<template>
  <div class="my-5">
    <h1>{{card.title}}</h1>
    <h2>{{card.original_title}}</h2>
    <h3>{{card.original_language}}</h3>
    <h4>{{card.score_average}}</h4>
  </div>
</template>

<script>
export default {
  name: "CardComp",
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