<template>
    <select class="options w-full">
      <option v-for="(option, index) in options" :value="option.key" :key="index">{{ option.name }}</option>
    </select>
</template>
  
<script>
export default {
  props: {
    options: {
      type: Array,
      required: true
    },
  },
};
</script>

<style lang="scss" scoped>
.options {
  background-color: rgb(72, 72, 72);
  border-radius: 4px;
  padding: 5px 10px;
}
</style>