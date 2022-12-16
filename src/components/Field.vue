<template>
  <component v-if="typeof as === 'string'" :is="as" :name="name"
    @input="formikProvider.formSetData($event.target.value, name)" :value="formikProvider.formData.value[name]" />

  <component v-else :is="as" :name="name" :modelValue="formikProvider.formData.value[name]"
    v-on:update:modelValue="editData" />
</template>

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
    required: true
  }
});

const formikProvider = inject("formikProvider");

const editData = (newData) => {
  formikProvider.formSetData(newData, props.name);
};
</script>
