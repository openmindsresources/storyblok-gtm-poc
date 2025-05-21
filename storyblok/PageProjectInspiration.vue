<template>
  <main class="min-h-screen flex flex-col">
    <section class="flex-1 flex flex-col items-center justify-center bg-gray-50 py-16 px-4 text-center">
      <h2 class="text-2xl md:text-4xl font-bold mb-4">Get Inspired by Our Projects</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6 w-full max-w-3xl">
        <div v-for="project in projects" :key="project" class="bg-white rounded shadow p-6 flex flex-col items-center">
          <span class="text-lg font-semibold mb-2">{{ project.title }}</span>
          <a class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700" :href="project.url" @click="trackProject(project)">View Project</a>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const projects = ref([
  { title: 'Home Renovation', url: '/projects/home-renovation' },
  { title: 'Project Alpha', url: '/projects/project-alpha' },
])

onMounted(() => {
  // Simulate analytics: page view
  // window.dataLayer.push({ event: 'page_view', page: 'project_inspiration' })
})

function trackProject(project) {
  // Simulate analytics: project click
  // window.dataLayer.push({ event: 'project_click', project })
}
</script>

<!--
Layout: layout-projects-page.md
Analytics: page view (onMounted), project click
-->
