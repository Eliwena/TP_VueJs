<script setup>
import { inject, defineProps } from "vue";

const props = defineProps({
  as: {
    type: [String, Object],
    required: false,
    default: "input"
  },
  name: {
    type: String,
    required: true,
  },
});

//injecter les données de Formik
const formikProvide = inject("formik");
</script>

<template>
  <component v-if="typeof props.as === 'string'" :is="props.as" :name="props.name"
    :value="formikProvide.values[props.name]" @input="formikProvide.values" />
  <component v-else :is="props.as" :name="props.name" @input="formikProvide.values"></component>
</template>
