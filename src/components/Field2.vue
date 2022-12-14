<template>
  <input 
    :type="type"
    :name="name" 
    :id="name" 
    v-model="values"
  />
    <!-- <component :is="tag" v-bind="$attrs" v-on="$listeners" @input="updateValue" /> -->
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true
    },
    type: {
      type: String,
      default: 'text'
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
