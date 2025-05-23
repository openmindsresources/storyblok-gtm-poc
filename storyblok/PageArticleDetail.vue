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

    <div class="mw-3xl mx-auto mb-12">
      <h2 class="text-2xl font-bold mb-4">Related Articles</h2>
      <p class="mb-8 text-lg text-gray-600">Explore more articles related to this topic.</p>
      <ArticleList/>
    </div>
  </main>
</template>

<script setup>
</script>
