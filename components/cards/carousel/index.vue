<template>
  <div class="movie-card py-12">
    <div>
      <img :src="data.img" :alt="data.title">
    </div>

    <div class="movie-card__content">
      <h3>{{ data.title }}</h3>
      
      <p class="my-2">{{ data.year }}</p>

      <p>{{ data.description }}</p>
    </div>
  </div>
</template>
  
<script>
export default {
  props: {
    data: {
      type: Object,
      required: true
    }
  }
}
</script>
  
<style lang="scss" scoped>
.movie-card {
  align-items: center !important;
  color:#fff;
  display: flex !important;
  margin: 1rem auto;
  justify-content: center;

  &__content {
    background-color: #000;
    padding: 2rem;
    width: 40%;
  }

  img {
    width: 100%;
    max-height: 360px;
    object-fit: cover;
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
  }
}
</style>
