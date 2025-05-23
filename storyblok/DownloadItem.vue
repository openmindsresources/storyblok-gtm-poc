<template>
  <div class="flex-1 bg-white rounded shadow p-4 flex flex-col justify-between">
    <div>
      <div class="text-lg font-semibold text-blue-800 mb-1">{{ title }}</div>
      <div class="text-gray-600 text-sm mb-2">{{ description }}</div>
    </div>
    <a
      class="bg-blue-600 text-white px-6 py-2 rounded hover:bg-blue-700 mt-2 flex items-center justify-center gap-2"
      :data-filename="filename"
      :data-group="group"
      :href="url"
    >
      <DownloadIcon :size="18" color="#fff" />
      Download
  </a>
  </div>
</template>

<script setup>
import DownloadIcon from './DownloadIcon.vue'

const props = defineProps({
  title: String,
  description: String,
  filename: String,
  group: String,
  url: String,
})
</script>
