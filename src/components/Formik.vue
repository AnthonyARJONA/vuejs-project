<template>
  <slot :data="formData" :error="error" :isSubmitting="isSubmitting" :handleSubmit="submitMethod" />
</template>

<script setup>
import { ref, defineProps, provide, onMounted } from 'vue';

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
  }
});

const formData = ref(props.initialValues);

onMounted(() => {
  if (props.initialValues) {
    for (const item in props.initialValues) {
      formSetData(props.initialValues[item], item);
    }
  }
});

const submitMethod = () => {
  error.value = props.validate(formData.value);
  if (Object.keys(error.value).length === 0) {
    isSubmitting.value = true;
    props.onSubmit(formData.value);
  }
};

const formSetData = (newData, fieldName) => {
  formData.value[fieldName] = newData;
};

const error = ref([]);
const isSubmitting = ref(false);

provide("formikProvider", {
  formSetData,
  formData,
});

</script>
