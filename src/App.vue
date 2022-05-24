<template>
  <div>
    <HeaderComp @search="iniziaRicerca" />
    <div class="main-body">
      <MainComp v-if="movieArray.length > 0" itemTitle="Films:" :itemFilmArray="movieArray"/>
      <MainComp v-if="tvArray.length > 0" itemTitle="Serie Tv:" :itemTvArray="tvArray"/>
      <h3 class="cerca-film d-flex justify-content-center align-items-center" v-if="movieArray.length == 0 && tvArray.length == 0 ">CERCA UN FILM!</h3>
    </div>
    
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
      this.movieArray = []
      this.tvArray = []
      this.apiParams.query = text;
      if(text.length > 0) this.getMovieApi();
      
      if(text.length > 0)this.getTvApi();
    }
  },
}


</script>

<style lang="scss">
@import './assets/style/_vars.scss';
@import './assets/style/_general.scss';
@import './assets/style/_utils.scss';

.cerca-film {
  font-weight: bold;
  color: rgb(232, 39, 32);
  padding-top: 300px;
}
</style>
