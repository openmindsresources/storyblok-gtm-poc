<template>
    <div v-editable="blok">
        {{ blok.body }}
    </div>
</template>

<script setup>
defineProps({
    blok: Object,
});
</script>

<style scoped>
/* Add your styles here */
</style>