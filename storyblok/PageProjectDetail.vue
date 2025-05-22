<template>
  <main class="min-h-screen flex flex-col bg-white">
    <!-- Hero Banner -->
    <section class="relative flex items-center justify-center h-64 md:h-96 bg-indigo-600 text-white mb-12">
      <div class="absolute inset-0 bg-cover bg-center opacity-30" style="background-image: url('https://images.unsplash.com/photo-1465101178521-c1a9136a3b99?auto=format&fit=crop&w=1200&q=80');"></div>
      <div class="relative z-10 text-center">
        <h1 class="text-4xl md:text-6xl font-extrabold drop-shadow mb-2">Project Detail</h1>
        <p class="text-lg md:text-2xl font-medium drop-shadow">A showcase of a featured project.</p>
      </div>
    </section>

    <!-- Project Overview -->
    <section class="max-w-4xl mx-auto px-4 mb-8">
      <h2 class="text-2xl font-bold mb-4 text-indigo-700">Project Overview</h2>
      <p class="text-gray-700 text-lg leading-relaxed">This section provides a generic overview of the project, its goals, and its outcomes. Replace this with actual project information as needed.</p>
    </section>

    <!-- Gallery -->
    <section class="max-w-4xl mx-auto px-4 mb-8">
      <h2 class="text-2xl font-bold mb-4 text-indigo-700">Gallery</h2>
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
        <img v-for="img in gallery" :key="img" :src="img" class="rounded shadow object-cover w-full h-32" />
      </div>
    </section>

    <!-- Related Projects -->
    <section class="max-w-4xl mx-auto px-4 mb-12">
      <h2 class="text-2xl font-bold mb-4 text-indigo-700">Related Projects</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div v-for="project in relatedProjects" :key="project.title" class="bg-white rounded shadow p-6 flex flex-col items-start">
          <h3 class="text-xl font-semibold mb-2">{{ project.title }}</h3>
          <p class="text-gray-600 mb-4">{{ project.summary }}</p>
          <a class="bg-indigo-600 text-white px-4 py-2 rounded hover:bg-indigo-700" :href="project.url" @click="trackRelated(project.title)">View Project</a>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const gallery = ref([
  'https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=400&q=80',
  'https://images.unsplash.com/photo-1465101046530-73398c7f28ca?auto=format&fit=crop&w=400&q=80',
  'https://images.unsplash.com/photo-1465101178521-c1a9136a3b99?auto=format&fit=crop&w=400&q=80',
  'https://images.unsplash.com/photo-1465101046530-73398c7f28ca?auto=format&fit=crop&w=400&q=80',
])
const relatedProjects = ref([
  { title: 'Project Alpha', summary: 'A modern residential project.', url: '/projects/project-alpha' },
])

onMounted(() => {
  // Simulate analytics: page view
  // window.dataLayer.push({ event: 'page_view', page: 'project_detail' })
})

function trackRelated(title) {
  // Simulate analytics: related project click
  // window.dataLayer.push({ event: 'related_project_click', project: title })
}
</script>

<!--
Layout: layout-project-detail.md
Analytics: page view (onMounted), related project click
-->
