<template>
    <div class="content">
        <div class="container-fluid">
            <div class="row">
                <div class="col-9 contentWrapper mt-5 mx-auto d-flex flex-wrap gap-3 align-items-start" v-if="searchValue!=null">
                    <card v-for="(film,index) in results" :key="index" :film="film"/>
                </div>
                <div v-if="noMovies==true&&noSeries==true" class="noResults col-12">
                    <h1 class="text-center text-danger">Non ci Sono risultati</h1>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import card from './Card.vue'
export default {
    name:'indexMain',
    components:{
        card,
    },
    props:{
        results:Array,
        searchValue:String,
        noMovies:Boolean,
        noSeries:Boolean
    }
}
</script>

<style lang="scss" scoped>
.content{
    background-color: rgba(61, 61, 61, 0);
}
</style>