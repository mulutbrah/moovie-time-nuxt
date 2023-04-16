<template>
    <div class="discover">
        <div class="blank">&nbsp;</div>

        <div class="discover-movies container mx-auto">
            <div class="flex justify-between items-center">
                <h3 class="title">Discover Movies</h3>

                <div class="flex items-center">
                    <button class="bg-red-600 hover:bg-red-700 text-white font-bold py-2 px-4 rounded-full mr-2">
                        Popularity
                    </button>

                    <button class="bg-stone-900 hover:bg-stone-950 text-white font-bold py-2 px-4 rounded-full">
                        Release Date
                    </button>
                </div>
            </div>

            <div class="grid grid-cols-5 gap-6">
                <cards :movie="movie" v-for="(movie, index) in movies" :key="index" />
            </div>
        </div>
    </div>
</template>

<script>
import { MOVIES } from "@/data/general";

export default {
    data: () => ({
        movies: MOVIES,
    }),
}
</script>

<style lang="scss" scoped>
.discover-movies {
    color: #fff;
    .title {
        font-size: 24px;
    }
}

.blank {
    background-color: rgb(72, 72, 72);
    height: 300px;
    margin-bottom: -230px;
    width: 100%;
}
</style>