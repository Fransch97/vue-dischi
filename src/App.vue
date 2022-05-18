<template>
  <div id="app">
    <AppHeader @custom="valoreSelct" :options="arrayGenere"/>
    <AppMain :cards="aggiornaArray"  />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios'

export default {
    components: { AppHeader,AppMain },
    data() {
      return {
            url: "https://flynn.boolean.careers/exercises/api/array/music",
            arrayResponse: [],
            arrayGenere: ["All"],
            selOpt:"All"
      }
    },

    computed: {
      aggiornaArray(){
      return this.arrayResponse.filter(obj=> obj.genre.includes(this.selOpt) ||  this.selOpt === "All"  )
      }
    },

    methods: {
      filterGen(array, genere){
        array.forEach(element => {
          if(!(genere.includes(element.genre))){
            genere.push(element.genre);
          }
        });

      },
      valoreSelct(valore){
        this.selOpt = valore
      }
    },

    mounted() {
      axios.get(this.url)
      .then( r =>{
        console.log(r.data.response);
        this.arrayResponse = r.data.response;
        this.filterGen(this.arrayResponse, this.arrayGenere);
      }
      )
    },
}




</script>


<style lang="scss" scoped>
@import "./assets/styles/global";
</style>
