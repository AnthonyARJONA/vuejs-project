<script setup>
  import ref from 'vue'

  let email = ref('')
  let password = ref('')
  let errors = ref({})
  let submitting = ref(false)

  const handleSubmit = () => {
    errors.value = validate()
    if (Object.keys(errors.value).length === 0) {
      submitting.value = true
      setTimeout(() => {
        alert(JSON.stringify({ email: email.value, password: password.value }, null, 2))
        submitting.value = false
      }, 400)
    }
  }
  
</script>

<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <input type="email" placeholder="Email" v-model="email" />
      <span v-if="errors.email">{{ errors.email }}</span>
      <input type="password" placeholder="Password" v-model="password" />
      <span v-if="errors.password">{{ errors.password }}</span>
      <button type="submit" :disabled="submitting">
        Submit
      </button>
    </form>
  </div>
</template>