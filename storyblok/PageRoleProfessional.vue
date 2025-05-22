<template>
  <main class="min-h-screen flex flex-col">
    <section class="flex-1 flex flex-col items-center justify-center py-16 px-4 text-center relative overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-br from-green-400 via-blue-200 to-white opacity-80"></div>
      <div class="absolute inset-0 bg-cover bg-center opacity-30" style="background-image: url('https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=1200&q=80');"></div>
      <div class="relative z-10 flex flex-col items-center">
        <h2 class="text-2xl md:text-4xl font-bold mb-4">Welcome, Professional!</h2>
        <p class="mb-8 text-lg text-gray-600">Discover solutions, case studies, and resources for professionals.</p>
        <a class="bg-green-600 text-white px-6 py-2 rounded hover:bg-green-700" :href="'/project-inspiration'" @click="trackCta">View Case Studies</a>
      </div>
    </section>
  </main>
</template>

<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  // Simulate analytics: page view
  // window.dataLayer.push({ event: 'page_view', page: 'role_professional' })
})

function trackCta() {
  // Simulate analytics: CTA click
  // window.dataLayer.push({ event: 'cta_click', label: 'View Case Studies' })
}
</script>

<!--
Layout: layout-professional.md
Analytics: page view (onMounted), CTA click
-->
