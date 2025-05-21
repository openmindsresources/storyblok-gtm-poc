<template>
  <main class="min-h-screen flex flex-col">
    <section class="flex-1 flex flex-col items-center justify-center bg-gray-50 py-16 px-4 text-center">
      <h2 class="text-2xl md:text-4xl font-bold mb-4">Other Projects</h2>
      <p class="mb-8 text-lg text-gray-600">Explore other project examples and solutions.</p>
    </section>
  </main>
</template>

<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  // Simulate analytics: page view
  // window.dataLayer.push({ event: 'page_view', page: 'segmentation_others' })
})
</script>

<!--
Layout: layout-projects-page.md
Analytics: page view (onMounted)
-->
