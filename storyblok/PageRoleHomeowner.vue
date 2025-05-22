<template>
  <main class="min-h-screen flex flex-col">
    <section class="flex-1 flex flex-col items-center justify-center bg-gray-50 py-16 px-4 text-center">
      <h2 class="text-2xl md:text-4xl font-bold mb-4">Welcome, Homeowner!</h2>
      <p class="mb-8 text-lg text-gray-600">Find inspiration, tips, and resources for your building journey.</p>
      <a class="bg-blue-600 text-white px-6 py-2 rounded hover:bg-blue-700" :href="'/project-inspiration'" @click="trackCta">Explore Ideas</a>
    </section>
  </main>
</template>

<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  // Simulate analytics: page view
  // window.dataLayer.push({ event: 'page_view', page: 'role_homeowner' })
})

function trackCta() {
  // Simulate analytics: CTA click
  // window.dataLayer.push({ event: 'cta_click', label: 'Explore Ideas' })
}
</script>

<!--
Layout: layout-professional.md
Analytics: page view (onMounted), CTA click
-->
