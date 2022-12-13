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
    // Dans votre composant Vue.js

    onSubmit() {
      // Récupération des valeurs des champs du formulaire
      const formFields = Object.values(this.$refs)

      // Booléen qui indique si le formulaire est valide
      let formIsValid = true

      // Itération sur les champs du formulaire
      formFields.forEach(field => {
        console.log(field.error)
        // Si le champ est vide, ajouter un message d'erreur
        if (field.value === '') {
          // edit prop field.error
          this.$refs.child.propName = 'newValue'
          formIsValid = false
        } else {
          // Sinon, supprimer le message d'erreur (s'il existe)
          this.$set(field, 'error', 'test')
        }
      })

      // Si le formulaire est valide, soumettre les données
      if (formIsValid) {
        // Soumettre les données du formulaire
      }
    }

  }
}
</script>

<template>
  <div>
    <Form @onSubmit="onSubmit">
      <Field ref="field1" id="field1" label="test" value="" type="text" error="" />
    </Form>
  </div>
</template>
