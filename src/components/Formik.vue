<template>
  <form @submit.prevent="handleSubmit">
    <slot :values="values" :errors="errors" :isSubmitting="isSubmitting" />
  </form>
</template>

<script>
import { ref } from 'vue';
export default {
  props: {
    name: {
      type: String,
      required: true
    },
    type: {
      type: String,
      default: 'text'
    },
    initialValues: {
      type: Object,
      required: false
    },
    validate: {
      type: Function,
      required: false
    },
    onSubmit: {
      type: Function,
      required: true
    }
  },
  
  setup(props, { emit }) {
    const values = ref(props.initialValues);
    const errors = ref({});
    const handleSubmit = (e) => {
      e.preventDefault();
      emit('onSubmit', e.target.value);
    };
    const isSubmitting = ref(false);

    return {
      values,
      errors,
      handleSubmit,
      isSubmitting
    };
  }
}
</script>
