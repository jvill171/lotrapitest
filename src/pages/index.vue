<script setup>
import {useAPI} from "../composables/useAPI";

const {movies, movie, getMovies} = useAPI();
movie.value = "";
</script>

<template>
  <div class="mt-16">
    <ul class="grid grid-cols-3 gap-12">
      <router-link
        class="bg-white rounded-lg shadow-2xl p-4 cursor-pointer hover:scale-105"
        v-for="movie in movies"
        :key="movie._id"
        :to="`/movie/${movie._id}`">
        <div>
          <h3 class="text-xl font-semibold tracking-tight">{{ movie.name }}</h3>
          <p>Runtime: {{ movie.runtimeInMinutes }} minutes</p>
          <p>Budget: ${{ movie.budgetInMillions }} million</p>
          <p>Score: {{ movie.rottenTomatoesScore }}</p>
        </div>
      </router-link>
    </ul>
  </div>

</template>
