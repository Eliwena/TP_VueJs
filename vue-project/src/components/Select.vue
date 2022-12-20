<script setup>

import { defineProps, provide, ref } from "vue";

const props = defineProps({
  options: {
    type: Array,
    required: true,
  },
  name: {
    type: String,
    required: true,
  },
});

</script>


<template>
    <select>
        <option v-for="option in props.options" :value="option.name">
            {{ option.name }}
        </option>
    </select>
</template>

<style scoped>
</style>