<template>
  <component v-if="typeof as === 'string'" :is="as" :name="name"
    @input="formikProvider.formSetData($event.target.value, name)" :value="formikProvider.formData.value[name]" />

  <component v-else :is="as" :name="name" :modelValue="formikProvider.formData.value[name]"
    v-on:update:modelValue="editData" />
</template>

<script setup>
import { inject, defineProps } from "vue";

// Define the props for the component
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

// Inject the 'formikProvider' function
const formikProvider = inject("formikProvider");

// Set the value of a field in the form data
const editData = (newData) => {
  // Use the 'formSetData' function from the 'formikProvider' to set the data
  formikProvider.formSetData(newData, props.name);
};
</script>
