<template>
  <div class="navbar">
    <div class="container mx-auto flex justify-between items-center h-full">
      <div class="cursor-pointer" @click="onHomePage">
        <logo-moovie-time />
      </div>
      <div>
        <searchbar placeholder="Find Movie" :value="search" @on:enter="onEnter" />
      </div>
      <div class="menu flex items-center justify-between">
        <div 
          class="flex items-center mr-4"
          v-for="(menu, index) in items" :key="index"
          @click="onRedirectMenu(menu.title)"
          >
          <component v-if="menu.title === 'MOVIES'" :is="menu.logo"  class="mr-1 cursor-pointer" />
          <component v-else :is="menu.logo"  class="mr-1 cursor-pointer"/>
          <span>{{ menu.title }}</span>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import { MENUS, MOVIES } from "@/data/general";
import CategoryIcon from '@/components/logo/category.vue';

export default {
  components: {
    CategoryIcon,
  },
  data: () => ({
    state: {
      loadingLogout: false,
    },
    items: MENUS,
    movies: MOVIES,
    search: ''
  }),
  methods: {
    onHomePage() {
      this.$router.push(`/`);
    },

    onRedirectMenu(menu) {
      if(menu === 'MOVIES') {
        this.$router.push(`/movies`);
      }
    },

    onGoBack() {
      this.$router.go(-1);
    },

    onEnter(value) {
      let res = this.movies.find(item => item.title.toLowerCase().includes(value))
      
      this.$router.push(`/movies/${res.slug}`)
    }
  },
};
</script>

<style lang="scss" scoped>
.navbar {
  background-color: rgb(72, 72, 72);
  height: 66px;
  width: 100%;

  .menu {
    color: #fff;
  }
}
</style>