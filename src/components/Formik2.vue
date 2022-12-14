<template>
  <form @submit.prevent="handleSubmit">
    <slot :values="values" />
  </form>
</template>

<script>
export default {
  props: {
    initialValues: {
      type: Object,
      default: () => ({})
    },
    validate: {
      type: Function,
      default: values => ({})
    },
    onSubmit: {
      type: Function,
      default: (values, actions) => { }
    }
  },
  data() {
    return {
      values: this.initialValues,
      errors: {},
      isSubmitting: false
    }
  },
  methods: {
    handleSubmit() {
      this.errors = this.validate(this.values);
      if (Object.keys(this.errors).length === 0) {
        this.submitting = true;
        this.onSubmit(this.values, { setSubmitting: value => this.submitting = value });
      }
    }
    // handleSubmit(event) {
    //     event.preventDefault()
    //     this.errors = this.validate(this.values)
    //     if (Object.keys(this.errors).length === 0) {
    //       this.isSubmitting = true
    //       this.onSubmit(this.values)
    //         .then(() => (this.isSubmitting = false))
    //         .catch(() => (this.isSubmitting = false))
    //     }
    //   }
  }
}

</script>