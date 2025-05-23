<template>
  <main class="min-h-screen flex flex-col">
    <section class="flex-1 flex flex-col items-center justify-center bg-gray-50 py-16 px-4 text-center">
      <h2 class="text-2xl md:text-4xl font-bold mb-4">Get Inspired by Our Projects</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6 w-full max-w-3xl">
        <div v-for="item in projectList?.data?.stories" :key="item.id" class="bg-white rounded shadow p-6 flex flex-col items-center">
          <span class="text-lg font-semibold mb-2">{{ item.name }}</span>
          <a class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700" :href="'/'+item.full_slug" 
            v-bind:data-label="item.name"
            data-tag="view_project_click">View Project</a>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
const projectList = await useStoryblokApi().get('cdn/stories', {
  "version": "draft",
  "starts_with": "projects",
})
</script>
