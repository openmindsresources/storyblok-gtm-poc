<template>
     <div class="download-list">
          <DownloadButton v-for="blok in blok.body" :key="blok._uid" :blok="blok" />
     </div>
</template>

<script setup>
defineProps({ blok: Object });
</script>