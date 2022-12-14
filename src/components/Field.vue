<template>
  <component 
    :is="as"
    v-bind="$attrs" 
    v-on="$listeners" 
    @input="updateValue" 
    :id="name"
    :name="name" 
    :value="value"
    :type="type"
  />
</template>

<script>
export default {
  props: {
    as: {
      type: String,
      default: 'input'
    },
    name: {
      type: String,
      required: true
    },
    value: {
      type: String,
      required: false,
    },
    type: {
      type: String,
      required: false
    }
  },
}
</script>
