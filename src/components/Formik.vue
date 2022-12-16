<template>
  <slot :data="formData" :error="error" :isSubmitting="isSubmitting" :handleSubmit="submitMethod" />
</template>

<script setup>
import { ref, defineProps, provide, onMounted } from 'vue';

// Define the props for the component
const props = defineProps({
  onSubmit: {
    type: Function,
    required: true,
  },
  initialValues: {
    type: Object,
    required: false,
  },
  validate: {
    type: Function,
    required: false,
  },
});

// Initialize a reactive variable to store the form data
const formData = ref(props.initialValues);

// Set the initial values of the form when the component is mounted
onMounted(() => {
  if (props.initialValues) {
    for (const item in props.initialValues) {
      formSetData(props.initialValues[item], item);
    }
  }
});

// Submit the form by calling the 'onSubmit' prop function and passing in the form data
const submitMethod = () => {
  // Validate the form data using the 'validate' prop function
  error.value = props.validate(formData.value);
  // If there are no errors, submit the form by calling the 'onSubmit' prop function
  if (Object.keys(error.value).length === 0) {
    isSubmitting.value = true;
    props.onSubmit(formData.value);
  }
};

// Set the value of a field in the form data
const formSetData = (newData, fieldName) => {
  formData.value[fieldName] = newData;
};

// Initialize reactive variables to store the form errors and the submitting state
const error = ref([]);
const isSubmitting = ref(false);

// Provide the 'formikProvider' function with the form data and the 'formSetData' function
provide("formikProvider", {
  formSetData,
  formData,
});

</script>
