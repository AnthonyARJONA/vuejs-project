<template>
  <div class="field">
    <input :name="name" :value="values[name] ?? ''" />
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true
    },
    value: {
      type: Object,
      required: true
    }
  },
  data() {
    value: {}
  },
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
