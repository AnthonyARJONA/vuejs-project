<template>
  <form>
    <slot />
  </form>
</template>

<script>
import ref from 'vue'

export default {
  data() {
    const values = ref({})
    const errors = ref({})
    const isSubmitting = ref(false)
  },
  
  methods: {
    initialValues() {
      console.log('initialValues()', this.$slots.default)
    },
    validate() {},
    onSubmit() {},

    values() {}, 
    errors() {}, 
    handleSubmit() {}, 
    isSubmitting() {}
  }
  
}
</script>
