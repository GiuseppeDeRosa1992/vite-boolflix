<script>
import store from "../data/store.js";
import CreatedMovies from './CreatedMovies.vue';
import CreatedTvSeries from "./CreatedTvSeries.vue";

export default {
    components: {
        CreatedMovies,
        CreatedTvSeries,
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
        <!-- SEZIONE MOVIES -->
        <section id="card" class="container mb-2">
            <h2 class="m-0 text-center bg-danger"> {{ store.film
                }} </h2>
            <div class="content-card text-white mt-2">
                <div class="row m-0 flex-wrap">
                    <CreatedMovies v-for="list in store.movieList" :card="list" />
                </div>
            </div>
        </section>

        <!-- SEZIONE SERIE TV -->
        <section id="card" class="container">
            <h2 class="m-0 text-center bg-danger"> {{
                store.serieTv }} </h2>
            <div class="content-card text-white mt-2">
                <div class="row flex-wrap m-0">
                    <CreatedTvSeries v-for="list in store.tvList" :cardTv="list" />
                </div>
            </div>
        </section>
    </main>
</template>

<style></style>