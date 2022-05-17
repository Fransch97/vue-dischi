<template>
<main>
    <div class="container main">
        <AppCard v-for="(obj, ind) in cards"  :key="`card-${ind}`" :card="obj"/>
    </div>
</main>
  
</template>

<script>
import  axios from "axios";
import AppCard from "./AppCard.vue";
export default {
    name: "AppMain",
    comments: "axios",
    data() {
        return {
            url: "https://flynn.boolean.careers/exercises/api/array/music",
            cards: Array
        };
    },
    methods: {
        api() {
            axios.get(this.url)
                .then(api => {
                console.log(api.data.response);
                this.cards = api.data.response;
                console.log(this.cards, "le card");
            });
        }
    },
    mounted() {
        this.api();
    },
    components: { AppCard }
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
}
</style>