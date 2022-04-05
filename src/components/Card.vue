<template>
    <div class="text text-center">
        <h6 class="px-3">
            {{film.title}}
        </h6>
        <h6 class="px-3">
            {{film.original_title}}
        </h6>
        <h6 class="px-3">
            {{film.original_language}} <lang-flag :iso="film.original_language" />
        </h6>
        <h6 class="px-3">
            {{film.vote_average}}
        </h6>
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
    }
}
</script>

<style>

</style>