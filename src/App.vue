<template>
  <div>
    <HeaderComp @search="iniziaRicerca" />
    <MainComp :itemArray="movieArray"/>
    <MainComp :tvArray="tvArray"/>
  </div>
  

 
</template>

<script>
import axios from "axios";
import MainComp from "./components/MainComp.vue";
import HeaderComp from "./components/HeaderComp.vue";


export default {
  name: 'App',

  
  components: {
    MainComp,
    HeaderComp
  },

data() {
  return {
    apiUrl: 'https://api.themoviedb.org/3/search/movie',
    apiUrlTv: 'https://api.themoviedb.org/3/search/tv',
    apiParams:{
      api_key: '07c6ae64f440609bbe4618623c458175',
      language: 'it-IT',
      query: ''
    },
    movieArray: [],
    tvArray: [],
   
  }
},

methods: {
  getMovieApi(){
    axios.get(this.apiUrl,{
      params: this.apiParams,
    })
    .then(res => {
      console.log(res.data);
      this.movieArray = res.data.results;
      console.log(this.movieArray);
    })
    .catch(err => {
      console.log(err);
    })
      console.log(this.params);
  },

  getTvApi(){
    axios.get(this.apiUrlTv,{
      params: this.apiParams,
    })
    .then(res => {
      console.log(res.data);
      this.tvArray = res.data.results;
      console.log(this.tvArray);
    })
    .catch(err => {
      console.log(err);
    })
      console.log(this.params);
  },

  iniziaRicerca(text){
    this.apiParams.query = text;
    this.getMovieApi();
    this.getTvApi();
  }

},


}


</script>

<style lang="scss">

</style>
