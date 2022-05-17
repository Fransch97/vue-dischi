<template>
  <div class="card-sc">
      <img :src="card.poster" alt="card.title" :class="card.genre">
      <p>{{card.title}}</p>
      <span>{{card.author}}</span>
  </div>
</template>

<script>
export default {
    name: "AppCard",
    props:{
        card: Object
    }

}
</script>

<style lang="scss">
@import "../assets/styles/card";
</style>