<template>
  <header>
    <div class="logo">
      <img :src="img" alt="">
      </div>
    <select v-model="selectedOption" @change="$emit('custom', selectedOption)" class="form-select sele-sc" aria-label="Default select example">
      <option v-for="(el, index) in options" :key="`opt-${index}`" :value="el">{{el}}</option>
  
    </select> 
  </header>
</template>

<script>
export default {
    name: "AppHeader",
    props:{
      options: Array
    },
    data(){
      return{
        img: require("../assets/img/spt.png"),
        selectedOption: "All"
        
      }
    }
}
</script>

<style lang="scss" >
@import "../assets/styles/header";
@import "../assets/styles/global";

</style>