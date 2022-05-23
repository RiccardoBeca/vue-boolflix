<template>
  <div>
    <HeaderComp @search="iniziaRicerca" />
    <MainComp itemTitle="Films" :itemFilmArray="movieArray"/>
    <MainComp itemTitle="Serie Tv" :itemTvArray="tvArray"/>
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
    if(text.length > 0) this.getMovieApi();
    else this.movieArray = [];    
    
    if(text.length > 0)this.getTvApi();
    else this.tvArray = [];    

  }

},


}


</script>

<style lang="scss">

</style>
