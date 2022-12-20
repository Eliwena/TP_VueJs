<script setup>
import { unref, ref } from "vue";
const props = defineProps({
  options: {
    type: Array,
    required: true,
  },
  value: {
    type: Object,
    required: true,
  },
  name: {
    type: String,
    required: true,
  },
});

const emit = defineEmits({
  "update:value": function validate(value) {
    return typeof value === "object" && value.id && value.src;
    },
});


const handleClick = (option) => {
  emit("update:value", unref(option));
  //passer a true selected pour l'image cliqué 
  console.log(option)

  //emit("toto", { target: { value: option, name: props.name } });
};
</script>

<template>
  <div class="grid">
    <img
      :class="{ selected: option.id == value?.id }"
      v-for="option in options"
      :src="option.src"
      @click="handleClick(option)"
    />
  </div>
</template>



<style scoped>
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 10px;
}
.selected {
  border: 2px solid green;
}
</style>
