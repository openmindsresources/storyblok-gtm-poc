<template>
  <main class="min-h-screen flex flex-col">
    <!-- Hero Section -->
    <section class="flex-1 flex flex-col items-center justify-center py-16 px-4 text-center relative overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-br from-blue-500 via-blue-300 to-white opacity-80"></div>
      <div class="absolute inset-0 bg-cover bg-center opacity-30" style="background-image: url('https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=1200&q=80');"></div>
      <div class="relative z-10 flex flex-col items-center">
        <h2 class="text-2xl md:text-4xl font-bold mb-4">Homepage</h2>
        <p class="mb-8 text-lg text-gray-600">Simulating Google Tag Manager & Analytics events for demo purposes.</p>
      </div>
    </section>

    <!-- Role Selection Modal -->
    <div v-if="showModal" class="fixed inset-0 z-50 flex items-center justify-center bg-black bg-opacity-40">
      <div class="bg-white rounded-lg shadow-lg p-8 w-full max-w-md relative">
        <button @click="showModal = false" data-tag="modal_dissmiss" class="absolute top-2 right-2 text-gray-400 hover:text-gray-700 text-2xl font-bold">&times;</button>
        <h3 class="text-xl font-semibold mb-6">Choose</h3>
        <div class="flex flex-col gap-4">
          <a class="bg-blue-600 text-white px-6 py-2 rounded hover:bg-blue-700" :href="'/role/homeowner'" data-tag="audience_select">I'm a Homeowner</a>
          <a class="bg-green-600 text-white px-6 py-2 rounded hover:bg-green-700" :href="'/role/professional'" data-tag="audience_select">I'm a Professional</a>
          <a class="bg-yellow-600 text-white px-6 py-2 rounded hover:bg-yellow-700" :href="'/role/contractor'" data-tag="audience_select">I'm a Contractor</a>
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
import { ref } from 'vue'

const showModal = ref(true)
</script>
