<template>
  <header>
    <div class="logo">
      <img :src="img" alt="">
    </div>
    
    <div class="selectores">
      <select v-model="selectedOption" @change="$emit('custom', selectedOption)" class="form-select sele-sc" aria-label="Default select example">
        <option v-for="(el, index) in optionsGenere" :key="`opt-${index}`" :value="el">{{el}}</option>
      </select> 
      <select v-model="selectedAuthor" @change="$emit('custom', selectedOption)" class="form-select sele-sc" aria-label="Default select example">
        <option v-for="(el, index) in optionsAuthor" :key="`opt-${index}`" :value="el">{{el}}</option>
    
      </select>
    </div>
  </header>
</template>

<script>
export default {
    name: "AppHeader",
    props:{
      optionsGenere: Array,
      optionsAuthor: Array,
    },
    data(){
      return{
        img: require("../assets/img/spt.png"),
        selectedOption: "All",
        selectedAuthor: "Authors"
        
      }
    }
}
</script>

<style lang="scss" >
@import "../assets/styles/header";
@import "../assets/styles/global";
.selectores{
  display: flex;
  select{
    margin-right: 10px ;
  }
}

</style>