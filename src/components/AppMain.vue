<template>
<main>
    <div v-if="loader" class="container main">
        <AppCard v-for="(obj, ind) in cards"  :key="`card-${ind}`" :card="obj"/>
    </div>
    <div v-else class="loader">
        <AppLoader />
    </div>
</main>
  
</template>

<script>
import  axios from "axios";
import AppCard from "./AppCard.vue";
import AppLoader from "./AppLoader.vue";
export default {
    name: "AppMain",
    comments: "axios",
    data() {
        return {
            url: "https://flynn.boolean.careers/exercises/api/array/music",
            cards: Array,
            loader: false
        };
    },
    methods: {
        api() {
            axios.get(this.url)
                .then(api => {
                console.log(api.data.response);
                this.cards = api.data.response;
                console.log(this.cards, "le card");
                this.loader = true
            });
        }
    },
    mounted() {
        this.api();
    },
    components: { AppCard, AppLoader }
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