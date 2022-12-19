<script setup>
import { defineProps, provide, ref } from "vue";

const props = defineProps({
  initialValues: {
    type: Object,
    required: false,
  },
  validate: {
    type: Function,
    required: false,
  },
  onSubmit: {
    type: Function,
    required: true,
  },
});


const data = ref(props.initialValues);


const errors = ref([]);
const isSubmitting = ref(false);

//envoyer les données a fields 
const submitEnd = () => {
  if (props.validate) {
    console.log(data.value)
    errors.value = props.validate(data.value);
  }
  if (Object.keys(errors.value).length === 0) {
    isSubmitting.value = true;
    console.log("ccc")
    props.onSubmit();
  }
}

const newData = (value, name) => {
  data.value[name] = value;
};


// const isSubmitting = ref(true);

provide("formik", {
  data,
  newData,
});


</script>

<template>
  <slot
    :values="data"
    :errors="errors"
    :isSubmitting="isSubmitting"
    :handleSubmit="submitEnd"
  ></slot>
</template>
