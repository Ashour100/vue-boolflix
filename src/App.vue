<template>
  <div id="app">
    <Header @search="assign"/>
    <Main :results="result" :searchValue="searchValue" />
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
      result:null,
      query:null,
    }
  },
  methods:{
        getApiData(){
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=78fc62f1828b567ef5fc7ae26f10d923&query='+this.searchValue)
            .then((result)=>{
              this.result=result.data.results;
                  console.log(this.result);
            });
            console.log(this.searchValue+"searchValue")
        },
        assign: function(value){
          this.searchValue=value;       
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
  mounted: function(){
    this.getApiData();
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
}
</style>
