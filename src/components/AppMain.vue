<template>
<main>
    <div  class="container main">
        <AppCard v-for="(obj, ind) in cards"  :key="`card-${ind}`" :card="obj"/>
    </div>
    
</main>
  
</template>

<script>
import AppCard from "./AppCard.vue";
export default {
    components: { AppCard,  },
    name: "AppMain",
    props:{
            cards: Array,
    },
    
    
}
</script>

<style lang="scss">
main{
    padding: 50px;
    .main{
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
    }
    .loader{
        text-align: center;
}
}
</style>