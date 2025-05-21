<template>
  <main class="min-h-screen flex flex-col bg-white">
    <!-- Hero Banner -->
    <section class="relative flex items-center justify-center h-64 md:h-96 bg-gradient-to-r from-purple-600 to-purple-400 text-white mb-12">
      <div class="absolute inset-0 bg-cover bg-center opacity-30" style="background-image: url('https://images.unsplash.com/photo-1465101178521-c1a9136a3b99?auto=format&fit=crop&w=1200&q=80');"></div>
      <div class="relative z-10 text-center">
        <h1 class="text-4xl md:text-6xl font-extrabold drop-shadow mb-2">E-Library</h1>
        <p class="text-lg md:text-2xl font-medium drop-shadow">Download resources and guides for your projects.</p>
      </div>
    </section>

    <!-- Download List -->
    <section class="max-w-4xl mx-auto px-4 mb-12">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div v-for="item in downloads" :key="item.title" class="bg-white rounded shadow p-6 flex flex-col items-start">
          <h3 class="text-xl font-semibold mb-2">{{ item.title }}</h3>
          <p class="text-gray-600 mb-4">{{ item.description }}</p>
          <button class="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700" @click="trackDownload(item.title)">Download</button>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const downloads = ref([
  { title: 'Product Brochure', description: 'Comprehensive guide to our product range.' },
  { title: 'Installation Manual', description: 'Step-by-step installation instructions.' },
])

onMounted(() => {
  // Simulate analytics: page view
  // window.dataLayer.push({ event: 'page_view', page: 'e_library' })
})

function trackDownload(title) {
  // Simulate analytics: download click
  // window.dataLayer.push({ event: 'download_click', label: title })
}
</script>

<!--
Layout: layout-e-library.md
Analytics: page view (onMounted), download click
-->
