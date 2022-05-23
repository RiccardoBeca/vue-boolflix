<template>

  <div class="d-flex justify-content-center">
    <div class="container">
      <div class="row">
        <!-- searchbar -->
        <div class="col d-flex">
           <input v-model="bindingQuery"  @keyup.enter="sendEmit" class="form-control" type="text" placeholder="Cerca un film">
        </div>

        <!-- select -->
        <div class="col">
            <select class="custom-select">
              <option value="">Scegli una categoria</option>
              <option value="Film">Film</option>
              <option value="Serie Tv">Serie Tv</option>
            </select>
        </div>
      </div>
    </div>
  </div>

  
</template>

<script>
export default {
  name: "HeaderComp",
  data() {
    return {
      bindingQuery: '',
    }
  },
  
  methods:{
    sendEmit(){
      this.$emit('search', this.bindingQuery);
      this.bindingQuery = "";
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/_vars.scss';
@import '../assets/style/_general.scss';
@import '../assets/style/_utils.scss';
</style>