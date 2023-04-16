<template>
  <div class="flex justify-evenly items-center navbar">
    <div>
      <logo-moovie-time />
    </div>
    <div>
      <searchbar placeholder="Find Movie" />
    </div>
    <div class="menu flex items-center justify-between">
      <div 
        class="flex items-center mr-4"
        v-for="(menu, index) in items" :key="index">
        <component :is="menu.logo"  class="mr-1"/>
        <span>{{ menu.title }}</span>
      </div>
    </div>
  </div>
</template>

<script>
import { MENUS } from "@/data/general";
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
  }),
  methods: {
    onProfile() {
      this.$router.push(`/categories`);
    },

    onGoBack() {
      this.$router.go(-1);
    },
  },
};
</script>

<style lang="scss" scoped>
.navbar {
  background-color: rgb(72, 72, 72);
  height: 66px;
  padding: 0 120px;
  width: 100%;

  .menu {
    color: #fff;
  }
}
</style>