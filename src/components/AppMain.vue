<script>
import store from "../data/store.js";
import CreatedMovies from './CreatedMovies.vue'

export default {
    components: {
        CreatedMovies,
    },

    data() {
        return {
            store,
        }
    },

    methods: {

    },
}
</script>

<template>
    <main>
        <CreatedMovies />
    </main>
</template>

<style></style>