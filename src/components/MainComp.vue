<template>
  <div>
    <CardComp :card="card" v-for="(card, index) in itemArray" :key="`card${index}`"/>
  </div>
  
</template>

<script>
import CardComp from './CardComp.vue';

  export default {
    name: "MainComp",
    props: {
      itemArray: Array,
    },
    components: { CardComp }
  }
</script>

<style lang="scss" scoped>
</style>



