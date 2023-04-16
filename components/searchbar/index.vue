<template>
    <div class="searchbar flex items-center">
        <logo-movie class="searchbar__logo" />
        <input v-model="searchTerm" class="searchbar__input" type="text" :placeholder="placeholder"
            @keyup.enter="onEnter"
        >
    </div>
</template>

<script>
export default {
    props:{
        placeholder: {
            type: String,
            default: () => ''
        },
    },

    data() {
        return {
            searchTerm: '',
        };
    },

    methods: {
        onEnter() {
            this.$emit('on:enter', this.searchTerm)
        }
    }
}
</script>

<style lang="scss" scoped>
.searchbar {
    height: 36px;
    padding: 12px 0 12px 30px;
    position: relative;
    width: 571px;

    &__input {
        background-color: rgb(60 60 60);
        border-radius: 4px;
        color: #fff;
        padding: 5px 0 5px 45px;
        width: 100%;
    }

    &__logo {
        position: absolute;
        left: 40px;
    }
}
</style>