<template>
  <div id="app">
    <Header @search="assign"/>
    <Main :results="allResults" :searchValue="searchValue" :noMovies="noMovies" :noSeries="noSeries"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/main.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data:function(){
    return{
      searchValue:null,
      movieResult:[],
      tvResult:[],
      allResults:null,
      query:null,
      noMovies:null,
      noSeries:null,
    }
  },
  methods:{
        getApiData(){
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=78fc62f1828b567ef5fc7ae26f10d923&query='+this.searchValue)
            .then((result)=>{
              this.movieResult=result.data.results;
                  console.log(this.movieResult);
                  if(this.movieResult.length!=0)
                    this.noMovies=false;
                  else
                    this.noMovies=true;
            });
            axios.get('https://api.themoviedb.org/3/search/tv?api_key=78fc62f1828b567ef5fc7ae26f10d923&query='+this.searchValue)
            .then((result)=>{
              this.tvResult=result.data.results;
                  console.log(this.tvResult);
                  if(this.tvResult.length!=0)
                    this.noSeries=false;
                  else
                    this.noSeries=true;
            });
              this.allResults=[...this.movieResult, ...this.tvResult];
            console.log(this.searchValue+"searchValue")
        },
        assign: function(value){
          this.searchValue=value;
          if(value.trim()!="")
            this.getApiData();
        },
        formQuery:function(){
          if(this.searchValue!=null){
            let temp=this.searchValue.split(' ');
            for(let i=0;i<temp;i++){
              if(i!=temp.length-1)
                this.searchValue+=temp+"+";
              else
                this.searchValue+=temp;  
            }
          }
        }
  },
  updated: function(){
    this.formQuery();
  }
}
</script>

<style lang="scss">
@import 'assets/scss/style.scss';
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background-color: $gray-800;
  min-height:100vh ;
}
</style>
