<template>
     <DownloadButton v-for="blok in blok.body" :key="blok._uid" :blok="blok" />
</template>

<script lang="ts" setup>
defineProps({ blok: Object });
</script>