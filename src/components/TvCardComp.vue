<template>

  <div class="p-2 my-2">
    <div class="flip-card">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <!-- ciclo le copertine dei film concatenando url di base con il path immagine dinamico tramite binding -->
          <img v-if="card.poster_path" :src="`https://image.tmdb.org/t/p/w342${card.poster_path}`" alt="copertina">
          <!-- se non trovo immagini stampo un'immagine di riserva -->
          <img v-else src="../assets/img/1889142.jpg" alt="">
        </div>
        <div class="flip-card-back p-5">
          <!-- con questo v-if/v-else evito di stampare titoo/titolo originale due volte nel caso essi fossero uguali -->
          <!--  -->
          <h2 v-if="card.original_name === card.name">{{card.name}}</h2>
          <h2 v-else>{{card.original_name}}</h2>
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
          <p>{{card.overview}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TvCardComp",
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

.flip-card {
  background-color: transparent;
  width: 300px;
  height: 450px;
  perspective: 1000px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform .8s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-card-front {
  background-color: #bbb;
  color: black;
  img{
    width: 300px;
    height: 450px;
  }
}

.flip-card-back {
  background-color: #252525;
  color: white;
  transform: rotateY(180deg);
  overflow-y: auto;
}

</style>