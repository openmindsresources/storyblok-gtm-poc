<template>
  <main class="min-h-screen flex flex-col bg-white">
    <!-- Hero Banner -->
    <section class="relative flex items-center justify-center h-64 md:h-96 bg-blue-600 text-white mb-12">
      <div class="absolute inset-0 bg-cover bg-center opacity-30" style="background-image: url('https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=1200&q=80');"></div>
      <div class="relative z-10 text-center">
        <h1 class="text-4xl md:text-6xl font-extrabold drop-shadow mb-2">About Us</h1>
        <p class="text-lg md:text-2xl font-medium drop-shadow">Learn more about our company, our team, and our journey.</p>
      </div>
    </section>

    <!-- Company Overview -->
    <section class="max-w-4xl mx-auto px-4 mb-12">
      <h2 class="text-2xl font-bold mb-4 text-blue-700">Company Overview</h2>
      <p class="text-gray-700 text-lg leading-relaxed">
        We are a forward-thinking company committed to delivering innovative solutions and exceptional value to our clients. Our mission is to empower people and organizations through quality products, integrity, and a passion for excellence. Our core values are trust, collaboration, and continuous improvement.
      </p>
    </section>

    <!-- Our Team -->
    <section class="max-w-5xl mx-auto px-4 mb-12">
      <h2 class="text-2xl font-bold mb-4 text-blue-700">Our Team</h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-8">
        <div v-for="member in team" :key="member.name" class="flex flex-col items-center bg-gray-50 rounded-lg shadow p-6">
          <img :src="member.photo" :alt="member.name" class="w-24 h-24 rounded-full mb-4 object-cover border-4 border-blue-200" />
          <h3 class="text-lg font-semibold">{{ member.name }}</h3>
          <p class="text-blue-600">{{ member.role }}</p>
        </div>
      </div>
    </section>

    <!-- Our History -->
    <section class="max-w-4xl mx-auto px-4 mb-12">
      <h2 class="text-2xl font-bold mb-4 text-blue-700">Our History</h2>
      <ol class="relative border-l-2 border-blue-200 ml-4">
        <li v-for="milestone in history" :key="milestone.year" class="mb-8 ml-6">
          <span class="absolute -left-3 flex items-center justify-center w-6 h-6 bg-blue-600 rounded-full text-white font-bold">{{ milestone.year }}</span>
          <div class="bg-white p-4 rounded shadow ml-2">
            <h4 class="font-semibold text-blue-700">{{ milestone.title }}</h4>
            <p class="text-gray-600">{{ milestone.description }}</p>
          </div>
        </li>
      </ol>
    </section>

    <!-- Call to Action -->
    <section class="flex flex-col items-center justify-center py-12 bg-blue-50">
      <h2 class="text-2xl font-bold mb-4 text-blue-700">Get in Touch</h2>
      <p class="mb-6 text-gray-700 text-lg">Interested in working with us or have questions? Reach out today!</p>
      <a href="/contact-us" class="bg-blue-600 text-white px-8 py-3 rounded-lg font-semibold shadow hover:bg-blue-700 transition" @click="trackCta">Contact Us</a>
    </section>
  </main>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const team = ref([
  { name: 'Alice Johnson', role: 'CEO', photo: 'https://randomuser.me/api/portraits/women/44.jpg' },
  { name: 'Bob Smith', role: 'CTO', photo: 'https://randomuser.me/api/portraits/men/32.jpg' },
  { name: 'Carol Lee', role: 'Head of Design', photo: 'https://randomuser.me/api/portraits/women/65.jpg' },
])
const history = ref([
  { year: 2015, title: 'Founded', description: 'Company was founded with a vision to innovate.' },
  { year: 2018, title: 'First Major Milestone', description: 'Reached 100+ clients and expanded our team.' },
  { year: 2022, title: 'Global Expansion', description: 'Opened offices in 3 new countries.' },
])

onMounted(() => {
  // Simulate analytics: page view
  // window.dataLayer.push({ event: 'page_view', page: 'about_us' })
})

function trackCta() {
  // Simulate analytics: CTA click
  // window.dataLayer.push({ event: 'cta_click', label: 'Contact Us' })
}
</script>

<!--
Layout: layout-about-us.md
Analytics: page view (onMounted), CTA click
-->
