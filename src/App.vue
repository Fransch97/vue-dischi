<template>
  <div id="app">
    <AppHeader @generes="valoreSelctGen" :optionsGenere="arrayGenere" :optionsAuthor="arrayAuthor"/>
    <AppMain @authors="valorSelectAutors" :cards="aggiornaArray"  />
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
            arrayAuthor: ["Authors"],
            selOpt:"All",
            selAut:"Authors"
      }
    },

    computed: {
      aggiornaArray(){
      return this.arrayResponse.filter(obj=> (obj.genre.includes(this.selOpt) || this.selOpt === "All") && (obj.author.includes(this.selAut) || this.selAut === "Authors"))
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
      filterAuthor(array, genere){
        array.forEach(element => {
          if(!(genere.includes(element.author))){
            genere.push(element.author);
          }
        });

      },
      valoreSelctGen(valore){
        this.selOpt = valore
        console.log("sono ", this.selOpt)
      },
      valorSelectAutors(valore){
        this.selAut = valore
        console.log("sono ", this.selAut)
      }
    },

    mounted() {
      axios.get(this.url)
      .then( r =>{
        console.log(r.data.response);
        this.arrayResponse = r.data.response;
        this.filterGen(this.arrayResponse, this.arrayGenere);
        this.filterAuthor(this.arrayResponse, this.arrayAuthor)
      }
      )
    },
}




</script>


<style lang="scss" scoped>
@import "./assets/styles/global";
</style>
