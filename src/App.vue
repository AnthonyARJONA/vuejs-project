<script setup>
import Formik from "./components/Formik.vue";
import Field from "./components/Field.vue";

// A function to submit the form data
const onSubmit = (formData) => {
  alert("Form submitted. Data : " + JSON.stringify(formData));
};

// The initial values for the form fields
const initialValues = {
  email: '',
  password: '',
  message: ''
};

// A function to validate the form data
const validate = (formData) => {
  // An object to store the errors
  const errors = {};
  if (formData.email.length < 6) {
    errors["email"] = "Email is too short";
  }
  if (formData.password.length < 6) {
    errors["password"] = "Password is too short";
  }
  if (formData.message.length < 3) {
    errors["message"] = "Message is too short";
  }
  // Return the errors object
  return errors;
};
</script>

<template>
  <div>

    <Formik :initialValues="initialValues" :validate="validate" :onSubmit="onSubmit"
      v-slot="{ error, handleSubmit, isSubmitting }">
      <form @submit.prevent="handleSubmit">
        <h1>Formik Form</h1>

        <Field type="email" :name="'email'" />
        <Field type="password" :name="'password'" />
        <Field as="textarea" :name="'message'" />

        <button type="submit" :disabled="isSubmitting">Submit</button>

        <div v-for="err in error">
          <p>{{ err }}</p>
        </div>
      </form>
    </Formik>
  </div>
</template>
