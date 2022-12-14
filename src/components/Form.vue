<template>
    <form @submit.prevent="onSubmit">
        <slot />
        <button type="submit">Envoyer</button>
    </form>
</template>

<script>
export default {
    methods: {        
        initialValues() {
            const formFields = Object.values(this.$refs);
            formFields.forEach(field => {
                this.$set(field, "value", "");
                this.$set(field, "error", null);
            });
        },
        onSubmit() {
            this.$emit("onSubmit");
            /*defineEmits(() => {
              // this.$emit("onSubmit");
              if     
            })*/
        }
    }
};
</script>