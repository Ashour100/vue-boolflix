<template>
<div class="container-fluid">
    <div class="row p-3 bg-dark align-items-center">
        <div class="logo col-2 text-danger">
            <h1 class="m-0">BOOLFLIX</h1>
        </div>
        <div class="col-2 ms-auto">
            <div class="input-group">
                <input type="text" 
                class="form-control me-2 rounded shadow-none" 
                placeholder="Search" 
                v-model="inputTextSearch"
                @keydown="$emit('search',inputTextSearch)"
                @keyup="$emit('search',inputTextSearch)"
                >
            </div>
        </div>
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