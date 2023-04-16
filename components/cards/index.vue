<template>
  <div class="movie-card cursor-pointer" @click="onRedirectTo(movie.slug)">
    <div class="movie-card__image">
      <div class="rating">{{ movie.rating }}</div>
      <img :src="movie.img" :alt="movie.title">
    </div>

    <h3>{{ movie.title }}</h3>
    <p>{{ movie.year }}</p>
  </div>
</template>
  
<script>
export default {
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
