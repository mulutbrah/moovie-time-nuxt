<template>
    <div class="discover">
        <div class="blank">&nbsp;</div>

        <div class="discover-movies container mx-auto pb-5">
            <div class="flex justify-between items-center">
                <h3 class="title">Movies</h3>
            </div>

            <div class="flex">
                <div class="mr-3 pt-3">
                    <movies-filter @on:click="updateQueryParam" />
                </div>

                <div>
                    <div class="grid grid-cols-5 gap-6">
                        <cards :movie="movie" v-for="(movie, index) in filtered_movies" :key="index" 
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
        filtered_movies: MOVIES
    }),

    computed: {
        queryParams() {
            return this.$route.query;
        }
    },

    watch: {
        queryParams: {
            handler() {
                this.filterData();
            },
            immediate: true,
            deep: true
        }
    },

    created() {
        this.filterData();
    },

    methods: {
        onRedirectTo(slug) {
            this.$router.push(`/movies/${slug}`)
        },

        onLoadMoreMovies() {
            this.movies = this.movies.concat(MOVIES)
        },

        filterData() {
            const query = this.$route.query;

            this.filtered_movies = this.movies

            const filteredData = this.filtered_movies.filter(item => {
                if (query.genres && query.genres.length > 0) {
                    const matches = item.genre.filter(genre => query.genres.includes(genre));
                    
                    if (matches.length === 0) {
                        return false;
                    }
                }

                return true;
            });

            this.filtered_movies = filteredData;
        },

        updateQueryParam(value) {
            const currentQuery = this.$route.query;
            const newQuery = { ...currentQuery };

            newQuery.genres = value;

            this.$router.push({ query: newQuery });
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