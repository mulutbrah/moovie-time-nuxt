<template>
  <div class="vue-app">
    <nav>
      <navbar />
    </nav>
    <main class="container">
      <Nuxt />
    </main>
    <footer>
      <moovie-footer />
    </footer>
  </div>
</template>

<style lang="scss" scoped>
.vue-app {
  background-color: rgb(60 60 60);

  .container {
    padding: 0 120px;
  }
}
</style>
