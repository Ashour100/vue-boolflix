<template>
    <div class="text text-center">
        <h6 class="px-3">
            {{film.title}}
        </h6>
        <h6 class="px-3">
            {{film.original_title}}
        </h6>
        <h6 class="px-3">
            {{film.original_language}}
        </h6>
        <h6 class="px-3">
            {{film.vote_average}}
        </h6>
    </div>
</template>

<script>
export default {
    name:"bodyCard",
    props:{
        film:Object,
    }
}
</script>

<style>

</style>