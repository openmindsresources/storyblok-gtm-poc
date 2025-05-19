<template>
     <div class="download-list flex flex-row justify-center items-center gap-4" v-editable="blok">
          <DownloadButton v-for="blok in blok.body" :key="blok._uid" :blok="blok" />
     </div>
</template>

<script setup>
defineProps({ blok: Object });
</script>