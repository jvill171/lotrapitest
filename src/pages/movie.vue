<script setup>
import {useRoute} from "vue-router";
import { useAPI } from "../composables/useAPI";

const router=useRoute();

const {id} = router.params;

const {movie, getMovie, quotes, getQuotes} = useAPI();

getMovie(id);
getQuotes(id);
</script>

<template>
    <div
     v-if="movie"
     class="bg-white text-center rounded-lg py-8 mt-16 max-w-sm mx-auto">
        <h3 class="text-xl font-semibold tracking-tight">{{ movie.name }}</h3>
        <p>Runtime: {{ movie.runtimeInMinutes }} minutes</p>
        <p>Budget: ${{ movie.budgetInMillions }} million</p>
        <p>Score: {{ movie.rottenTomatoesScore }}</p>
    </div>
    <div v-else>Loading...</div>
    <div class="mt-8">
        <p class="bg-white px-4 py-6 my-4 italic rounded-lg text-center text-lg" v-for="quote in quotes" :key="quote._id">{{quote.dialog}}</p>
    </div>
</template>
