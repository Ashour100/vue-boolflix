<template>
    <div class="content">
        <div class="container-fluid">
            <div class="row">
                <div class="col-9 contentWrapper mt-5 mx-auto d-flex flex-wrap gap-3 align-items-start" v-if="searchValue!=null">
                    <card v-for="(film,index) in results" :key="index" :film="film"/>
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
        searchValue:String
    }
}
</script>

<style lang="scss" scoped>
.content{
    background-color: rgba(61, 61, 61, 0);
}
</style>