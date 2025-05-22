<template>
  <main class="min-h-screen flex flex-col bg-white">
    <!-- Hero Banner -->
    <section class="relative flex items-center justify-center h-64 md:h-96 bg-blue-700 text-white mb-12">
      <div class="absolute inset-0 bg-cover bg-center opacity-30" style="background-image: url('https://images.unsplash.com/photo-1465101178521-c1a9136a3b99?auto=format&fit=crop&w=1200&q=80');"></div>
      <div class="relative z-10 text-center">
        <h1 class="text-4xl md:text-6xl font-extrabold drop-shadow mb-2">Product Name</h1>
        <p class="text-lg md:text-2xl font-medium drop-shadow">A generic product detail page for simulation.</p>
      </div>
    </section>

    <!-- Product Overview -->
    <section class="max-w-4xl mx-auto px-4 mb-8">
      <h2 class="text-2xl font-bold mb-4 text-blue-700">Product Overview</h2>
      <p class="text-gray-700 text-lg leading-relaxed">This section provides a generic overview of the product, its features, and its benefits. Replace this with actual product information as needed.</p>
    </section>

    <!-- Specifications -->
    <section class="max-w-4xl mx-auto px-4 mb-8">
      <h2 class="text-2xl font-bold mb-4 text-blue-700">Specifications</h2>
      <ul class="list-disc pl-6 text-gray-700">
        <li>Specification 1</li>
        <li>Specification 2</li>
        <li>Specification 3</li>
      </ul>
    </section>

    <!-- Downloads -->
    <DownloadSection title="Technical Datasheet" type="technicalDatasheet" />

    <DownloadSection title="Brochure" type="brochure" />
  </main>
</template>

<script setup>
import { onMounted } from 'vue'
import DownloadSection from './DownloadSection.vue'

onMounted(() => {
  // Simulate analytics: page view
  // window.dataLayer.push({ event: 'page_view', page: 'product_detail' })
})

function trackDownload(label) {
  // Simulate analytics: download click
  // window.dataLayer.push({ event: 'download_click', label })
}
</script>

<!--
Layout: layout-product.md
Analytics: page view (onMounted), download click
-->
