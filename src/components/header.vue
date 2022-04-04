<template>
    <div class="col-5 mx-auto">
        <div class="input-group">
                        <input type="text" class="form-control me-2 rounded shadow-none" placeholder="Search" v-model="value">
                        <button
                        type="button"
                        @click="$emit=('search',value)"
                        class="btn btn-primary rounded shadow-none">Search</button>
                    </div>
    </div>
</template>

<script>
export default {
    name:'indexHeader',
    data:function(){
        return{
            value:"ss",
        }
    },
}
</script>

<style lang="scss" scoped>

</style>