<script setup>
import Formik from "./components/Formik.vue";
import Field from "./components/Field.vue";
import { ref } from "vue";

let email     = ref('monsuperemail@gmail.com');
let password  = ref('monsuperpassword');
let message   = ref('');
</script>

<template>
  <div>
    <Formik 
      :initialValues="{ email, password }"
      :validate="validate"
      @onSubmit="handleSubmit"
    >
      <Field name="email" :value="email" type="email" as="input"/>
      <Field name="password" type="password" as="input" />
      <Field name="message" as="textarea" />

      <button type="submit" :disabled="submitting">Submit</button>
    </Formik>
  </div>
</template>

<script>
const handleSubmit = () => {
  console.log('submit', email.value, password.value, message.value);
};
</script>
