<template>
    <div v-if="film.poster_path!=null" class="card text-center">
        <img :src="imgSrc" alt="">
        <div class="overlay">
        <span v-if="film.title">Titolo: {{film.title}}</span>
        <span v-else>Titolo: {{film.name}}</span>
        <br>
        <span v-if="film.original_title" >Titolo originale: {{film.original_title}}</span>
        <span v-else>Titolo originale: {{film.original_name}}</span>
        <br>
        <span class="flag"><lang-flag :iso="film.original_language" /></span>
        <br>
        <span v-if="film.vote_average>0">Voto:
            <span v-for="(star,index) in 5" :key="index">
                <font-awesome-icon v-if="(index<film.vote_average / 2)" icon="fa-solid fa-star" />
            </span>
        </span>
        </div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags'
export default {
    name:"bodyCard",
    components: {
        LangFlag
    },
    props:{
        film:Object,
    },
    data:function(){
        return{
            imgSrc:"https://image.tmdb.org/t/p/w185"+this.film.poster_path,
        }
    },
    updated: function(){
        this.imgSrc="https://image.tmdb.org/t/p/w185"+this.film.poster_path;
    }
}
</script>
<style lang="scss" scoped>
.card{
    width: 172px;
    cursor:pointer;
    &:hover{
        .overlay{
            display: flex;
            flex-direction: column;
            align-items:center ; 
            }
    }
}
.overlay{
    display: none;
    position: absolute;
    background-color: rgba(12, 12, 12, 0.663);
    height: 100%;
    width: 100%;
    color: white;
    padding: 2rem 0;
    font-size: small;
}
</style>