<template>
    <div class="discover">
        <div class="blank">&nbsp;</div>

        <div class="discover-movies container mx-auto pb-5">
            <div class="flex justify-between items-center">
                <h3 class="title">Movies</h3>
            </div>

            <div class="flex">
                <div class="mr-3 pt-3">
                    <movies-filter />
                </div>

                <div>
                    <div class="grid grid-cols-5 gap-6">
                        <cards :movie="movie" v-for="(movie, index) in movies" :key="index" 
                            @on:redirect="onRedirectTo(movie.slug)"
                        />
                    </div>

                    <div class="mx-auto text-center">
                        <button class="bg-red-600 hover:bg-red-700 text-white font-bold py-2 px-4 rounded-full mr-2" @click="onLoadMoreMovies">
                            Load More
                        </button>
                    </div>
                </div>
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

    methods: {
        onRedirectTo(slug) {
            this.$router.push(`/movies/${slug}`)
        },

        onLoadMoreMovies() {
            this.movies = this.movies.concat(MOVIES)
        }
    },
}
</script>

<style lang="scss" scoped>
.discover-movies {
    color: #fff;
    .title {
        font-size: 24px;
        padding-top: 10px;
        border-top: solid 3px #E74C3C;;
    }
}

.blank {
    background-color: rgb(72, 72, 72);
    height: 300px;
    margin-bottom: -230px;
    width: 100%;
}
</style>