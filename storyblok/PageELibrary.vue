<template>
  <main class="min-h-screen flex flex-col bg-white">
    <!-- Hero Banner -->
    <section class="relative flex items-center justify-center h-64 md:h-96 bg-purple-600 text-white mb-12">
      <div class="absolute inset-0 bg-cover bg-center opacity-30" style="background-image: url('https://images.unsplash.com/photo-1465101178521-c1a9136a3b99?auto=format&fit=crop&w=1200&q=80');"></div>
      <div class="relative z-10 text-center">
        <h1 class="text-4xl md:text-6xl font-extrabold drop-shadow mb-2">E-Library</h1>
        <p class="text-lg md:text-2xl font-medium drop-shadow">Download resources and guides for your projects.</p>
      </div>
    </section>

    <!-- Download List -->
    <DownloadSection title="Technical Datasheet" type="technicalDatasheet" disableViewAll="true"/>

    <DownloadSection title="Brochure" type="brochure" disableViewAll="true"/>
  </main>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import DownloadSection from './DownloadSection.vue'

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
