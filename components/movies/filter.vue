<template>
  <div class="movies-filter divide-y">
    <div>
        <p class="name pb-3">Sort result by</p>
    </div>

    <div>
        <div class="py-4">
            <form-combobox :options="options" />
        </div>
    </div>

    <div>
        <p class="name py-3">Genres</p>
    </div>

    <div>
        <div class="py-4">
            <form-radio :data="genres" @on:click="updateQueryParam" />
        </div>
    </div>
  </div>
</template>

<script>
import { SORT_MOVIES, GENRES } from "@/data/general";

export default {
    data: () => ({
        options: SORT_MOVIES,
        genres: GENRES
    }),

    methods: {
        updateQueryParam(value) {
            this.$emit('on:click', value)
        }
    }
}
</script>

<style lang="scss" scoped>
.movies-filter {
    border-radius: 8px;
    background-color: rgb(60 60 60);
    width: 240px;
    padding: 20px 18px;

    .name {
        font-style: normal;
        font-weight: 600;
        font-size: 16px;
        line-height: 20px;
        color: #E5E5E5;
    }
}
</style>