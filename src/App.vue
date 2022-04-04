<template>
  <div id="app">
    <Header @search="assign"/>
    <h1>{{value}}</h1>
    <Main/>
  </div>
</template>

<script>
import Header from './components/header.vue';
import Main from './components/main.vue';
// import axios from 'axios';


export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data:function(){
    return{
      value:null,
    }
  },
  methods:{
        // getApiData(){
        //     axios.get('https://api.themoviedb.org/3/movie/550?api_key=78fc62f1828b567ef5fc7ae26f10d923&query=ritorno+al+futuro')
            // .then((result)=>{
            //     this.content=result.data.response;
            //     console.log(this.content);
            // })
        // },
        assign:function(value){
          this.value=value;
        },
    }
}
</script>

<style lang="scss">
@import 'assets/scss/style.scss';
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
