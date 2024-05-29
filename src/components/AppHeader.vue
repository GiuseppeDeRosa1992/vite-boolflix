<script>
import store from "../data/store.js"

export default {
    data() {
        return {
            store,
        }
    },

    methods: {
        foundMovies() {
            this.store.searchInput
            console.log("cliccato", this.store.searchInput)
            this.store.searchInput = ""
        }
    },
}
</script>

<template>
    <header class="bg-warning p-2 text-center">
        <h1 class="m-0">Cerca il tuo film</h1>
        <input type="text" placeholder="Cerca" v-model="store.searchInput">
        <button @click="foundMovies()">Cerca</button>
    </header>
</template>

<style></style>