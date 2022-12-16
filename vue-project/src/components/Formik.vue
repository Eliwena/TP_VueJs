<script setup>
import { defineProps, provide, ref } from 'vue'

const props = defineProps({
    initialValues: {
        type: Object,
        required: true,
    },
    validate: {
        type: Function,
        required: false,
    },
    onSubmit: {
        type: Function,
        required: true,
    },
})



provide('formik', {
    values: ref(props.initialValues),
    errors: ref(props.validate),
    handleSubmit: ref(props.onSubmit),
})
</script>

<template>
    <slot :values="values" :errors="errors" :isSubmitting="isSubmitting" :handleSubmit="submitFinal"></slot>
</template>