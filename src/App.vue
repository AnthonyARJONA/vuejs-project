<script setup>
import Formik2 from "./components/Formik2.vue";
import Field2 from "./components/Field2.vue";
</script>

<template>
  <div>
    <Formik2 :initialValues="{ email: 'salut@gmail.com', password: 'qzd' }" :validate="validate"
      @onSubmit="handleSubmit">
      <Field2 name="email" type="email" />
      <button type="submit" :disabled="submitting">
        Submit
      </button>
    </Formik2>
  </div>
</template>

<script>
export default {
  methods: {
    validate() {
      const errors = {};
      if (!this.email) {
        errors.email = 'Required';
      } else if (!/^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i.test(this.email)) {
        errors.email = 'Invalid email address';
      }
      return errors;
    },
    handleSubmit() {
      this.errors = this.validate();
      if (Object.keys(this.errors).length === 0) {
        this.submitting = true;
        setTimeout(() => {
          alert(JSON.stringify({ email: this.email, password: this.password }, null, 2));
          this.submitting = false;
        }, 400);
      }
    }
  }
}
</script>
