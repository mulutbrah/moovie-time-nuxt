<template>
  <div class="container mx-auto">
    <VueSlickCarousel :arrows="true" :dots="false">
      <cards-carousel :data="movie" v-for="(movie, index) in movies" :key="index" />
    </VueSlickCarousel>
  </div>
</template>
  
<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
// optional style for arrows & dots
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

import { TOP_MOVIES } from "@/data/general";

export default {
  components: {
    VueSlickCarousel 
  },
  data() {
    return {
      movies: TOP_MOVIES,
    }
  },
}
</script>
  