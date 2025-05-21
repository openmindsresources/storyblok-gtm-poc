<template>
  <main class="min-h-screen flex flex-col bg-white">
    <!-- Hero Banner -->
    <section class="relative flex items-center justify-center h-64 md:h-96 bg-gradient-to-r from-green-600 to-green-400 text-white mb-12">
      <div class="absolute inset-0 bg-cover bg-center opacity-30" style="background-image: url('https://images.unsplash.com/photo-1465101178521-c1a9136a3b99?auto=format&fit=crop&w=1200&q=80');"></div>
      <div class="relative z-10 text-center">
        <h1 class="text-4xl md:text-6xl font-extrabold drop-shadow mb-2">Articles & News</h1>
        <p class="text-lg md:text-2xl font-medium drop-shadow">Stay updated with the latest articles and news.</p>
      </div>
    </section>

    <!-- Article List -->
    <section class="max-w-4xl mx-auto px-4 mb-12">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div v-for="article in articles" :key="article.title" class="bg-white rounded shadow p-6 flex flex-col items-start">
          <h3 class="text-xl font-semibold mb-2">{{ article.title }}</h3>
          <p class="text-gray-600 mb-4">{{ article.summary }}</p>
          <a class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700" :href="article.url" @click="trackArticle(article.title)">Read Article</a>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const articles = ref([
  { title: 'How to Choose the Right Product', summary: 'Tips and advice for selecting the best product for your needs.', url: '/resources-support/how-to-choose-the-right-product' },
  { title: 'Industry News: 2025 Trends', summary: 'A look at the latest trends and innovations in the industry.', url: '/resources-support/industry-news-2025-trends' },
])

onMounted(() => {
  // Simulate analytics: page view
  // window.dataLayer.push({ event: 'page_view', page: 'articles_list' })
})

function trackArticle(title) {
  // Simulate analytics: article click
  // window.dataLayer.push({ event: 'article_click', article: title })
}
</script>

<!--
Layout: layout-list-article-news.md
Analytics: page view (onMounted), article click
-->
