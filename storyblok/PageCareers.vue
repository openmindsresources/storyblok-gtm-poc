<template>
  <main class="min-h-screen flex flex-col">
    <section class="flex-1 flex flex-col items-center justify-center bg-gray-50 py-16 px-4 text-center">
      <h2 class="text-2xl md:text-4xl font-bold mb-4">Join Our Team</h2>
      <p class="mb-8 text-lg text-gray-600">This is a dummy careers page for analytics simulation.</p>
    </section>
  </main>
</template>

<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  // Simulate analytics: page view
  // window.dataLayer.push({ event: 'page_view', page: 'careers' })
})

function trackNav(label) {
  // Simulate analytics: navigation click
  // window.dataLayer.push({ event: 'nav_click', label })
}
</script>

<!--
Layout: layout-about-us.md
Analytics: page view (onMounted), nav clicks
-->
