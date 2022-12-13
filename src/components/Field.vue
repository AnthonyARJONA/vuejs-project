<template>
  <div class="field">
    <label :for="id">{{ label }}</label>
    <input :id="id" v-model="value" @input="updateValue" :type="type">
    <p v-if="showError" class="error">{{ error }}</p>
  </div>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      required: true
    },
    label: {
      type: String,
      required: true
    },
    value: {
      type: String,
      required: true
    },
    type: {
      type: String,
      required: true
    },
    error: {
      type: String,
      default: null,
    }
  },
  computed: {
    showError() {
      return this.error !== null;
    }
  },
  methods: {
    updateValue(event) {
      this.$emit('input', event.target.value);
    }
  }
}
</script>

<style>
.field {
  margin-bottom: 1rem;
}

.error {
  color: red;
}
</style>
