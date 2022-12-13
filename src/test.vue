<template>
  <div>
    <Form @submit="onSubmit" ref="form">
      <Field v-for="field in fields" :id="field.id" :label="field.label" :value="field.value" :error="field.error"
        :type="field.type" :rules="field.rules" />
    </Form>
  </div>
</template>

<script>
import { Form, Field } from 'vue-form-generator';

export default {
  components: {
    Form,
    Field
  },
  data() {
    return {
      fields: [
        { id: 'field1', name: 'field1', label: 'Username', value: '', type: 'text', error: null, rules: [
          { required: true, message: 'Username is required' },
          { min: 3, message: 'Username must be at least 3 characters' },
          { max: 32, message: 'Username cannot be more than 32 characters' }
        ] },
        { id: 'field2', name: 'field2', label: 'Email', value: '', type: 'email', error: null, rules: [
          { required: true, message: 'Email is required' },
          { type: 'email', message: 'Email must be a valid email address' }
        ] },
        { id: 'field3', name: 'field3', label: 'Password', value: '', type: 'password', error: null, rules: [
          { required: true, message: 'Password is required' },
          { min: 8, message: 'Password must be at least 8 characters' }
