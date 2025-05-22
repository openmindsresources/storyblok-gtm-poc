<template>
  <main class="min-h-screen flex flex-col bg-white">
    <!-- Hero Banner -->
    <section class="relative flex items-center justify-center h-64 md:h-96 bg-blue-600 text-white mb-12">
      <div class="absolute inset-0 bg-cover bg-center opacity-30" style="background-image: url('https://images.unsplash.com/photo-1465101178521-c1a9136a3b99?auto=format&fit=crop&w=1200&q=80');"></div>
      <div class="relative z-10 text-center">
        <h1 class="text-4xl md:text-6xl font-extrabold drop-shadow mb-2">Product & Application</h1>
        <p class="text-lg md:text-2xl font-medium drop-shadow">Explore our product and application offerings.</p>
      </div>
    </section>

    <!-- Filters -->
    <section class="max-w-4xl mx-auto px-4 mb-8">
      <div class="flex flex-wrap gap-4 justify-center mb-6">
        <select class="border rounded p-2">
          <option>All Types</option>
          <option>Type A</option>
          <option>Type B</option>
        </select>
        <select class="border rounded p-2">
          <option>All Applications</option>
          <option>Application X</option>
          <option>Application Y</option>
        </select>
      </div>
    </section>

    <!-- Product List -->
    <section class="max-w-4xl mx-auto px-4 mb-12">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <div v-for="product in products" :key="product" class="bg-white rounded shadow p-6 flex flex-col items-center">
          <span class="text-lg font-semibold mb-2">{{ product.name }}</span>
          <a class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700" @click="trackProduct(product)" :href="product.url">View Product</a>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const products = ref([
  { name: 'Smart Home Hub', url: '/products/smart-home-hub' },
  { name: 'Wireless Door Sensor', url: '/products/wireless-door-sensor' },
  { name: 'Smart Thermostat', url: '/products/smart-thermostat' }
])

onMounted(() => {
  // Simulate analytics: page view
  // window.dataLayer.push({ event: 'page_view', page: 'product_and_application' })
})

function trackProduct(product) {
  // Simulate analytics: product click
  // window.dataLayer.push({ event: 'product_click', product })
}
</script>

<!--
Layout: layout-product-and-application.md
Analytics: page view (onMounted), product click
-->
