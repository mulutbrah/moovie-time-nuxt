<template>
  <div class="movie-card cursor-pointer" 
  v-on:mouseenter="isHovered = true" v-on:mouseleave="isHovered = false" v-bind:class="{ 'hovered': isHovered }"
  >
    <div>
      <div class="relative">
        <div class="movie-card__image">
          <div class="rating">{{ movie.rating }}</div>
          <img :src="movie.img" :alt="movie.title">
        </div>

        <div v-if="isHovered" class="movie-card__hovered bg-slate-900 p-3 text-center flex flex-col justify-center items-center">
          <div class="text-xl flex items-center">
            <logo-star />
            
            <div class="ml-2">
              {{ movie.rating }}
            </div>
          </div>

          <div class="text-l py-7 font-semibold">
            Action
          </div>

          <button class="bg-red-600 hover:bg-red-700 text-white font-bold py-2 px-4 rounded-full w-28"
          @click="onRedirectTo(movie.slug)">
            View
          </button>
        </div>
      </div>

      <h3>{{ movie.title }}</h3>
      <p>{{ movie.year }}</p>
    </div>
  </div>
</template>
  
<script>
export default {
  data() {
    return {
      isHovered: false
    };
  },

  props: {
    movie: {
      type: Object,
      required: true
    },
  },

  methods: {
    onRedirectTo(val) {
      this.$emit('on:redirect', val)
    },
  },
}
</script>
  
<style lang="scss" scoped>
.movie-card {
  color:#fff;
  margin: 1rem;

  &__hovered {
    border-radius: 0.5rem;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
  }

  &__image {
    position: relative;

    .rating {
      background: rgba(30, 35, 43, 0.8);
      border-radius: 0 0.5rem 0 0;
      top: 0;
      right: 0;
      padding: 5px 10px;
      position: absolute;
    }
    
    img {
      width: 100%;
      max-height: 400px;
      object-fit: cover;
      border-radius: 0.5rem;
    }
  }

  h3 {
    margin-top: 0.5rem;
    font-style: normal;
    font-weight: 600;
    font-size: 16px;
  }

  p {
    font-style: normal;
    font-weight: 400;
    font-size: 14px;
    line-height: 17px;
    color: #929292;
    margin-bottom: 0px;
  }
}
</style>
