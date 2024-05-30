<script>
import store from "../data/store.js";

export default {
    props: ["card"],

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
    <div class="col-12 col-sm-6 col-md-4 col-lg-2 px-2 py-1 mb-2">
        <div class="m-0 h-100 py-1 bg-secondary opacity-75 text-dark">
            <figure class="m-0">
                <img :src="card.backdrop_path == null ? store.urlImageRandom : store.urlImage + card.backdrop_path"
                    class="card-img-top img-fluid" alt="">
            </figure>
            <div class="description py-2">
                <!-- TITOLO IN LINGUA ORIGINALE FILM -->
                <h6 class="card-text my-fs py-2 text-center">Titolo film in lingua originale:
                    <span class="text-white">{{ card.original_title }}</span>
                </h6>
                <!-- TITOLO DEL FILM IN LINGUA ITALIANA -->
                <h6 class="card-text my-fs py-2s text-center">Titolo film:
                    <span class="text-white">{{ card.title }}</span>
                </h6>
                <!-- VOTO DEL FILM FIXATO CON MASSIMO DUE NUMERI DOPO LA VIRGOLA E DIVISO 2 DA AVERE UN NUMERO DA 1 A 5 VISTO CHE ERA DA 1 A 10 -->
                <h6 class="card-text my-fs py-2s text-center">
                    Voti film:
                    <span class="text-white">{{ (card.vote_average / 2).toFixed(2) }}</span>
                    <!-- AGGIUNTA STELLE IN BASE AL VOTO E DIVISO PER 2 -->
                    <div class="text-center mb-1">
                        <span v-if="(card.vote_average / 2) >= 0.5">
                            <i class="fa-solid fa-star" style="color: #FFD43B;"></i>
                        </span>
                        <span v-if="(card.vote_average / 2) >= 1.5">
                            <i class="fa-solid fa-star" style="color: #FFD43B;"></i>
                        </span>
                        <span v-if="(card.vote_average / 2) >= 2.5">
                            <i class="fa-solid fa-star" style="color: #FFD43B;"></i>
                        </span>
                        <span v-if="(card.vote_average / 2) >= 3.5">
                            <i class="fa-solid fa-star" style="color: #FFD43B;"></i>
                        </span>
                        <span v-if="(card.vote_average / 2) >= 4.5">
                            <i class="fa-solid fa-star" style="color: #FFD43B;"></i>
                        </span>
                    </div>
                </h6>
                <!-- LINGUA ORIGINALE DEL FILM -->
                <h6 class="card-text my-fs py-2s text-center">Lingua film:
                    <span class="text-white">{{ card.original_language }}</span>
                </h6>

                <!-- BANDIERA ASSOCIATA ALLA LINGUA ORIGINALE DEL FILM -->
                <h6 class="card-text my-fs py-2s text-center" v-if="card.original_language == 'en'">
                    <img src="../assets/en.svg" class="w-25" alt="">
                </h6>
                <h6 class="card-text my-fs py-2s text-center" v-if="card.original_language == 'it'">
                    <img src="../assets/it.svg" class="w-25" alt="">
                </h6>
                <h6 class="card-text my-fs py-2s text-center" v-if="card.original_language == 'de'">
                    <img src="../assets/de.svg" class="w-25" alt="">
                </h6>
                <h6 class="card-text my-fs py-2s text-center" v-if="card.original_language == 'fr'">
                    <img src="../assets/fr.svg" class="w-25" alt="">
                </h6>
                <h6 class="card-text my-fs py-2s text-center" v-if="card.original_language == 'no'">
                    <img src="../assets/no.svg" class="w-25" alt="">
                </h6>
                <h6 class="card-text my-fs py-2s text-center" v-if="card.original_language == 'ja'">
                    <img src="../assets/jp.svg" class="w-25" alt="">
                </h6>
            </div>

        </div>
    </div>

</template>

<style scoped></style>