<script>
import store from "../data/store.js";
import axios from "axios";

export default {
    data() {
        return {
            store,

        }
    },

    methods: {
        //CREO FUNZIONE  PER FILM CHE RICHIAMO AL CLICK DEL BOTTONE
        foundMovies() {
            this.store.film = "Film Trovati";
            const options = {
                method: 'GET',
                //RICHIAMO URL PER I FILM (MOVIES) DA STORE.JS
                url: this.store.url,
                //DICO AL QUERY CHE è UGUALE AL VALORE CHE L'UTENTE DA ALL'INPUT
                params: { query: this.store.searchInput, language: 'it-IT' },
                headers: {
                    accept: 'application/json',
                    Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIxMDc2ZTE3MjRkMmRkN2Y3MmJlMWNlZmU2ZmM1ZDE2NSIsInN1YiI6IjY2NTcyMDI3MDI4NjVlY2VhYTU5OTY4MCIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.oertjiXySwkWZydHwZLqFcz-MMuUUC0oCzK4koKkyzo'
                },
            };

            //RICHIAMO AXIOS CON LA FUNZIONE DEL SITO API
            axios
                .request(options)
                .then((response) => {
                    console.log(response.data.results);
                    this.store.movieList = response.data.results
                    console.log("lista film", this.store.movieList)
                })
                .catch(function (error) {
                    console.error(error);
                });
        },

        // //CREO FUNZIONE  PER FILM CHE RICHIAMO AL CLICK DEL BOTTONE
        // foundMoviesOriginal() {
        //     this.store.film = "Film Trovati";
        //     const options = {
        //         method: 'GET',
        //         //RICHIAMO URL PER I FILM (MOVIES) DA STORE.JS
        //         url: this.store.urlPopular,
        //         //DICO AL QUERY CHE è UGUALE AL VALORE CHE L'UTENTE DA ALL'INPUT
        //         params: { page: 1, language: 'it-IT' },
        //         headers: {
        //             accept: 'application/json',
        //             Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIxMDc2ZTE3MjRkMmRkN2Y3MmJlMWNlZmU2ZmM1ZDE2NSIsInN1YiI6IjY2NTcyMDI3MDI4NjVlY2VhYTU5OTY4MCIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.oertjiXySwkWZydHwZLqFcz-MMuUUC0oCzK4koKkyzo'
        //         },
        //     };

        //     //RICHIAMO AXIOS CON LA FUNZIONE DEL SITO API
        //     axios
        //         .request(options)
        //         .then((response) => {
        //             console.log(response.data.results);
        //             this.store.originalListList = response.data.results
        //             console.log("lista film", this.store.originalListList)
        //         })
        //         .catch(function (error) {
        //             console.error(error);
        //         });
        // },

        //CREO FUNZIONE PER SERIE TV CHE RICHIAMO AL CLICK DEL BOTTONE
        foundTvSeries() {
            this.store.serieTv = "Serie TV Trovate";
            const options = {
                method: 'GET',
                //RICHIAMO URL PER I SERIE TV (TV) DA STORE.JS
                url: this.store.urlTv,
                //DICO AL QUERY CHE è UGUALE AL VALORE CHE L'UTENTE DA ALL'INPUT
                params: { query: this.store.searchInput, language: 'it-IT' },
                headers: {
                    accept: 'application/json',
                    Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIxMDc2ZTE3MjRkMmRkN2Y3MmJlMWNlZmU2ZmM1ZDE2NSIsInN1YiI6IjY2NTcyMDI3MDI4NjVlY2VhYTU5OTY4MCIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.oertjiXySwkWZydHwZLqFcz-MMuUUC0oCzK4koKkyzo'
                },
            };

            axios
                .request(options)
                .then((response) => {
                    console.log(response.data.results);
                    this.store.tvList = response.data.results
                    console.log("lista serie tv", this.store.tvList)
                })
                .catch(function (error) {
                    console.error(error);
                });
            this.store.searchInput = ""

        }
    },
}
</script>

<template>
    <header class="bg-black p-2 text-center mb-3">
        <nav class="row m-0 align-items-center">
            <div class="col-2 text-start">
                <h1 class="m-0 text-danger">BOOLFLIX</h1>
            </div>
            <div class="col-7 text-start p-0">
                <ul class="m-0 d-flex p-0">
                    <a :href=li v-for="li in store.navList" class="text-decoration-none text-white">
                        <li class="px-2" @click="foundMoviesOriginal()"> {{ li }} </li>
                    </a>
                </ul>
            </div>
            <div class="col-3 text-end">
                <input class="w-100" type="text" placeholder="Cerca e premi Invio" v-model="store.searchInput"
                    @keyup.enter="foundMovies(), foundTvSeries()">
            </div>
        </nav>
    </header>
</template>

<style scoped>
ul {
    list-style-type: none;
}
</style>