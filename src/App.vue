<template>

<MainComp/>

 
</template>

<script>
import axios from "axios";
import MainComp from "./components/MainComp.vue";


export default {
  name: 'App',
  components: {MainComp},

data() {
  return {
    apiUrl: 'https://api.themoviedb.org/3/search/movie',
    apiParams:{
      api_key: '07c6ae64f440609bbe4618623c458175',
      language: 'it-IT',
      query: 'harry potter'
    }
   
  }
},

methods: {
  getApi(){
    axios.get(this.apiUrl,{
      params: this.apiParams,
    })
    .then(res => {
      console.log(res.data);
    })
    .catch(err => {
      console.log(err);
    })
      console.log(this.params);
  }
},

mounted() {
  this.getApi();
},

}


</script>

<style lang="scss">

</style>
