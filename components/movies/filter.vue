<template>
  <div class="movies-filter divide-y">
    <div>
        <p>Sort result by</p>
    </div>

    <div>
        <div class="pt-3">
            <form-combobox :options="options" />
        </div>
    </div>
  </div>
</template>

<script>
import { SORT_MOVIES } from "@/data/general";

export default {
    data: () => ({
        options: SORT_MOVIES,
    }),
}
</script>

<style lang="scss" scoped>
.movies-filter {
    border-radius: 8px;
    background-color: rgb(60 60 60);
    width: 240px;
    padding: 20px 18px;
}
</style>