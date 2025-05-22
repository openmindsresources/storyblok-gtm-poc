<template>
  <div class="flex-1 bg-white rounded shadow p-4 flex flex-col justify-between">
    <div>
      <div class="text-lg font-semibold text-blue-800 mb-1">{{ title }}</div>
      <div class="text-gray-600 text-sm mb-2">{{ description }}</div>
    </div>
    <button
      class="bg-blue-600 text-white px-6 py-2 rounded hover:bg-blue-700 mt-2 flex items-center justify-center gap-2"
      :data-filename="randomFileName(filename)"
      @click="trackDownload(title)"
    >
      <DownloadIcon :size="18" color="#fff" />
      Download
    </button>
  </div>
</template>

<script setup>
import DownloadIcon from './DownloadIcon.vue'

const props = defineProps({
  title: String,
  description: String,
  filename: String,
})

function trackDownload(label) {
  // Simulate analytics: download click
  // window.dataLayer.push({ event: 'download_click', label })
}

function randomFileName(base) {
  const rand = Math.random().toString(36).substring(2, 8)
  const ext = base.substring(base.lastIndexOf('.'))
  const name = base.substring(0, base.lastIndexOf('.'))
  return `${name}_${rand}${ext}`
}
</script>
