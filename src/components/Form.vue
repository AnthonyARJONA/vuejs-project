<template>
    <form @submit.prevent="onSubmit">
        <slot />
        <button type="submit">Envoyer</button>
    </form>
</template>
<script>
export default {
    methods: {
        onSubmit() {
            this.$emit("onSubmit");
        }
    }
};
</script>