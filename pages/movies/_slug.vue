<template>
    <div class="movie-detail">
        <!-- banner -->
        <div class="movie-detail__banner">
            <img :src="movie_selected.banner" :alt="movie_selected.title" />
        </div>
        <!-- end of banner -->

        <!-- content -->
        <div class="container mx-auto pb-5 content">
            <div class="flex relative">
                <div class="movie-detail__image relative z-10">
                    <img :src="movie_selected.img" :alt="movie_selected.title" />
                </div>

                <div class="ml-5 mt-4">
                    <div class="mb-5">
                        <h5 class="text-sm">{{ movie_selected.year }}</h5>
                        <h5 class="text-3xl">{{ movie_selected.title }}</h5>
                        <h5 class="text-xs">
                            <span v-for="(genre, index) in movie_selected.genre" :key="index">
                                <span>{{ genre }}</span>
                                <span v-if="index !== movie_selected.genre.length - 1">, </span>
                            </span>
                        </h5>
                    </div>

                    <div class="movie-detail__divider grid grid-cols-5 divide-x">
                        <div>
                            <span>
                                {{ movie_selected.rating }}
                            </span>
                            <span>
                                USER SCORE
                                {{ movie_selected.votes }} VOTES
                            </span>
                        </div>
                        <div>{{ movie_selected.status }}</div>
                        <div>{{ movie_selected.lang }}</div>
                        <div>{{ movie_selected.budget }}</div>
                        <div>{{ movie_selected.production }}</div>
                    </div>

                    <!-- overview -->
                    <div class="movie-detail__overview">
                        <p class="text-red-600 mb-2 font-semibold">OVERVIEW</p>
                        <p>{{ movie_selected.description }}</p>
                    </div>
                    <!-- end of overview -->
                </div>
            </div>
        </div>
        <!-- end of content -->

        <!-- review -->
        <div class="container mx-auto movie-detail__reviews pb-12">
            <p class="text-red-600 mb-2 font-semibold mb-4">REVIEWS</p>

            <div class="grid grid-cols-2 gap-4">
                <div v-for="(item, index) in movie_selected.reviews" :key="index">
                    <div class="review-card">
                        <div class="grid grid-cols-2 gap-4">
                            <div class="flex items-center">
                                <div class="mr-2">
                                    <img class="rounded-full" src="https://via.placeholder.com/50x50" alt="profile pict">
                                </div>

                                <div>
                                    <p>{{ item.name }}</p>
                                    <p>{{ item.date }}</p>
                                </div>
                            </div>


                            <div class="text-3xl text-right">
                                <span>{{ item.rating }}</span>
                            </div>
                        </div>

                        <div class="mt-3">
                            <p>{{ item.content }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- end of review -->

        <!-- recomendation -->
        <div class="movie-detail__recomendation">
            <div class="container mx-auto grid grid-cols-5 gap-6">
                <cards :movie="movie" v-for="(movie, index) in recomendation_movies" :key="index" 
                    @on:redirect="onRedirectTo(movie.slug)"
                />
            </div>
        </div>
        <!-- end of recomendation -->
    </div>
</template>

<script>
import { MOVIES, TOP_MOVIES } from "@/data/general";

export default {
    async asyncData({ params }) {
        let slug = params.slug

        return { slug }
    },

    data: () => ({
        movies: MOVIES,
        movie_selected: {},
        recomendation_movies: TOP_MOVIES
    }),

    mounted() {
        this.fetch()
    },

    methods: {
        fetch() {
            this.movie_selected = this.movies.find((item) => item.slug === this.slug)
        },

        onRedirectTo(slug) {
            this.$router.push(`/movies/${slug}`)
        }
    },
}
</script>

<style lang="scss" scoped>
.movie-detail {
    background-color: #fff;
    color: #fff;

    .content {
        margin-top: -180px;
    }

    &__divider {
        background-color: rgba(0, 0, 0, 0.5);
        padding: 1.5rem 0;
        position: absolute;
        width: 100%;
        left: 0;
        padding-left: 270px;
        z-index: 0;
    }

    &__image {
        img {
            height: 500px;
            width: 100%;
            object-fit: contain;
        }
    }

    &__overview {
        color: #000;
        margin-top: 100px;
        width: 60%;
    }

    &__banner {
        img {
            width: 100%;
        }
    }

    &__reviews {
        color: #000;

        .review-card {
            background: #F9F9F9;
            box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.1);
            border-radius: 14px;
            padding: 20px;
        }
    }

    &__recomendation {
        background-color: rgb(60, 60, 60);
    }
}
</style>