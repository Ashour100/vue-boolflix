<template>
    <div class="col-5 mx-auto">
        <div class="input-group">
            <input type="text" 
            class="form-control me-2 rounded shadow-none" 
            placeholder="Search" 
            v-model="inputTextSearch"
            @keydown.enter="$emit('search',inputTextSearch)">
            <button
            type="button"
            @click="$emit('search',inputTextSearch)"
            class="btn btn-primary rounded shadow-none">Search</button>
        </div>
    </div>
</template>

<script>
export default {
    name:'indexHeader',
    data:function(){
        return{
            inputTextSearch:"",
        }
    },
}
</script>

<style lang="scss" scoped>

</style>