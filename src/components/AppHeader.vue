<template>
  <header>
    <div class="logo">
      <img :src="img" alt="">
      </div>
    <select class="form-select sele-sc" aria-label="Default select example">
      <option selected>Seleziona un genere</option>
    </select> 
  </header>
</template>

<script>
export default {
    name: "AppHeader",
    data(){
      return{
        img: require("../assets/img/spt.png")
      }
    }
}
</script>

<style lang="scss" >
@import "../assets/styles/header";
@import "../assets/styles/global";

</style>