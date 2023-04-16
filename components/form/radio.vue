<template>
  <div>
    <div class="flex items-center justify-between" v-for="(datum, index) in data" :value="datum.key" :key="index">
      <label :for="datum.key" class="mr-3">
        {{ datum.name }}
      </label>
      <input :id="datum.key" type="checkbox" 
      @click="updateQueryParam(datum.key)"
      class="form-checkbox h-5 w-5 text-indigo-600 order-last">
    </div>
  </div>
</template>
  
<script>
export default {
  props: {
    data: {
      type: Array,
      required: true
    },
  },

  methods: {
    updateQueryParam(value) {
      this.$emit('on:click', value)
    }
  }
};
</script>

<style lang="scss" scoped>
.options {
  background-color: rgb(72, 72, 72);
  border-radius: 4px;
  padding: 5px 10px;

  &:checked {
    background: #E74C3C;
    color:#fff;
  }
}
</style>