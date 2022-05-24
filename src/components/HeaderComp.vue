<template>

  <div class="header">
    <div class="container-fluid d-flex justify-content-between">
      
      <div class="text-danger d-flex align-items-center">
        <img src="https://www.romait.it/wp-content/uploads/2022/04/Netflix-logo.jpg" alt="netflix logo">
      </div>
      <!-- searchbar -->
      <div class=" d-flex p-3">
          <input v-model="bindingQuery"  @keyup.enter="sendEmit" class="form-control" type="text" placeholder="Cerca un film">
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

.header {
  background-color: black;
  padding: 0;
  img{
    width: 150px;
  }
}
</style>