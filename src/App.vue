<script setup>
import Field from "./components/Field.vue";
</script>

<script>
import Form from "./components/Form.vue";

export default {
  components: {
    Form
  },
  methods: {
    initialValues() {
      const formFields = Object.values(this.$refs);
      formFields.forEach(field => {
        this.$set(field, "value", "");
        this.$set(field, "error", null);
      });
    },
    onSubmit() {
      
    }
  }
}
</script>

<template>
  <div>
    <Form @onSubmit="onSubmit" initialValues="initialValues">
      <Field ref="field1" id="field1" label="test1" value="" type="text" error="" />
      <Field />
    </Form>
  </div>
</template>
