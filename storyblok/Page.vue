<template>
  <div v-editable="blok" class="px-4">
    <StoryblokComponent v-for="blok_item in blok.body" :key="blok_item._uid" :blok="blok_item" />
  </div>
</template>

<script setup>
defineProps({ blok: Object });
</script>
