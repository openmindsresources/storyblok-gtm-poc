<template>
  <main class="min-h-screen flex flex-col">
    <!-- Hero Section -->
    <section class="flex-1 flex flex-col items-center justify-center py-16 px-4 text-center relative overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-br from-blue-500 via-blue-300 to-white opacity-80"></div>
      <div class="absolute inset-0 bg-cover bg-center opacity-30" style="background-image: url('https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=1200&q=80');"></div>
      <div class="relative z-10 flex flex-col items-center">
        <h2 class="text-2xl md:text-4xl font-bold mb-4">Homepage</h2>
        <p class="mb-8 text-lg text-gray-600">Simulating Google Tag Manager & Analytics events for demo purposes.</p>
        <div class="flex flex-col md:flex-row gap-4 justify-center">
          <button class="bg-blue-600 text-white px-6 py-2 rounded hover:bg-blue-700" @click="selectRole('Homeowner')">I'm a Homeowner</button>
          <button class="bg-green-600 text-white px-6 py-2 rounded hover:bg-green-700" @click="selectRole('Professional')">I'm a Professional</button>
          <button class="bg-yellow-600 text-white px-6 py-2 rounded hover:bg-yellow-700" @click="selectRole('Contractor')">I'm a Contractor</button>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  // Simulate analytics: page view
  // window.dataLayer.push({ event: 'page_view', page: 'homepage' })
})

function selectRole(role) {
  // Simulate analytics: role selection
  // window.dataLayer.push({ event: 'select_role', role })
  // Redirect to role landing page
  if (role === 'Homeowner') window.location.href = '/role/homeowner'
  if (role === 'Professional') window.location.href = '/role/professional'
  if (role === 'Contractor') window.location.href = '/role/contractor'
}
</script>

<!--
Layout: layout-homepage.md
Analytics: page view (onMounted), role selection (button click)
-->

<!-- Use the same approach as PageAboutUs.vue: implement professional, sectioned layouts for each Page component based on its layout file and sitemap mapping. -->
