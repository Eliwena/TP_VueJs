<script setup>
import { inject, defineProps } from "vue";

const props = defineProps({
  as: {
    type: [String, Object],
    required: false,
    default: "input",
  },
  name: {
    type: String,
    required: true,
  },
});

console.log(props.as, props.name)
//injecter les données de Formik
const formikProvide = inject("formik");
console.log("formikProvide", formikProvide);

</script>

<template>
  <component
    v-if="typeof props.as === 'string'"
    :is="props.as"
    :name="props.name"
    :value="formikProvide.data.value[name]"
    @input="formikProvide.newData($event.target.value, name)"
  />
  <component
    v-else
    :is="props.as"
    :name="props.name"
    :value="formikProvide.data.value[name]"
    @input="formikProvide.newData($event.target.value, name)"
  ></component>
</template>


<style scoped>
input, select,textarea {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}



</style>