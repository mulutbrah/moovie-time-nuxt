<template>
  <div class="movie-card">
    <img :src="movie.img" :alt="movie.title">
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
    }
  }
}
</script>
  
<style lang="scss" scoped>
.movie-card {
  color:#fff;
  margin: 1rem;

  img {
    width: 100%;
    max-height: 400px;
    object-fit: cover;
    border-radius: 0.5rem;
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
