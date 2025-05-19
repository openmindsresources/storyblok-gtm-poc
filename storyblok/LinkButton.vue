<template>
  <div class="link-button" v-editable="blok">
    <a :href="'/'+blok.link.cached_url" class="link-button__link">{{ blok.label }}</a>
  </div>
</template>

<script setup>
defineProps({ blok: Object });
</script>

<style scoped>
.link-button {
  display: inline-block;
}
.link-button__link {
  text-decoration: none;
  color: #007bff;
}
</style>
