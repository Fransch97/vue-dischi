<template>
  <header>
    <div class="logo">
      <img :src="img" alt="">
    </div>
    
    <div class="selectores">
      <select
        name="selectedOption" 
        v-model="selectedOption" 
        @change="$emit('generes', selectedOption)" 
        class="form-select sele-sc" >
        <option v-for="(el, index) in optionsGenere" :key="`opt-${index}`" :value="el">{{el}}</option>
      </select> 
      <select 
        name="selectedAuthor" 
        v-model="selectedAuthor" 
        @change="$emit('authors', selectedAuthor)" 
        class="form-select sele-sc" 
      >
        <option v-for="(el, index) in optionsAuthor" :key="`autor-${index}`" :value="el">{{el}}</option>
    
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
    },
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