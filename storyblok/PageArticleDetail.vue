<template>
  <main class="min-h-screen flex flex-col bg-white">
    <!-- Hero Banner -->
    <section class="relative flex items-center justify-center h-64 md:h-96 bg-green-600 text-white mb-12">
      <div class="absolute inset-0 bg-cover bg-center opacity-30" style="background-image: url('https://images.unsplash.com/photo-1465101178521-c1a9136a3b99?auto=format&fit=crop&w=1200&q=80');"></div>
      <div class="relative z-10 text-center">
        <h1 class="text-4xl md:text-6xl font-extrabold drop-shadow mb-2">Article Title</h1>
        <p class="text-lg md:text-2xl font-medium drop-shadow">A captivating article or news headline goes here.</p>
      </div>
    </section>

    <!-- Article Content -->
    <section class="max-w-3xl mx-auto px-4 mb-12">
      <article class="prose lg:prose-xl">
        <h2>Article Content</h2>
        <p>This is a sample article content area. Replace this with the actual article or news content. Use headings, paragraphs, images, and lists as needed to make the content engaging and informative.</p>
        <ul>
          <li>Key point one</li>
          <li>Key point two</li>
          <li>Key point three</li>
        </ul>
      </article>
    </section>

    <!-- Related Articles -->
    <section class="max-w-4xl mx-auto px-4 mb-12">
      <h2 class="text-2xl font-bold mb-4 text-green-700">Related Articles</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div v-for="related in relatedArticles" :key="related.title" class="bg-white rounded shadow p-6 flex flex-col items-start">
          <h3 class="text-xl font-semibold mb-2">{{ related.title }}</h3>
          <p class="text-gray-600 mb-4">{{ related.summary }}</p>
          <button class="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700" @click="trackRelated(related.title)">Read More</button>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const relatedArticles = ref([
  { title: 'Sustainable Building Materials', summary: 'Explore the latest in eco-friendly construction.' },
  { title: '2025 Industry Outlook', summary: 'What to expect in the coming year.' },
])

onMounted(() => {
  // Simulate analytics: page view
  // window.dataLayer.push({ event: 'page_view', page: 'article_detail' })
})

function trackRelated(title) {
  // Simulate analytics: related article click
  // window.dataLayer.push({ event: 'related_article_click', article: title })
}
</script>

<!--
Layout: layout-article-news.md
Analytics: page view (onMounted), related article click
-->
