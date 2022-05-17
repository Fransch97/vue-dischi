<template>
<main>
    
</main>
  
</template>

<script>
import  axios from "axios";
export default {
    name: "AppMain",
    comments:"axios",
    data() {
        return {
            url: "https://flynn.boolean.careers/exercises/api/array/music",
            cards: Array
        }
    },
    methods: {
        api(){
            axios.get(this.url)
            .then(api =>{
                console.log(api.data.response)
                this.cards = api.data.response
                console.log(this.cards ,"le card")
            })
        }
    },
    mounted() {
        this.api()
    },
}
</script>

<style>

</style>