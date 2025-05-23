<template>
  <main class="min-h-screen flex flex-col bg-white">
    <!-- Hero Banner -->
    <section class="relative flex items-center justify-center h-64 md:h-96 bg-green-600 text-white mb-12">
      <div class="absolute inset-0 bg-cover bg-center opacity-30" style="background-image: url('https://images.unsplash.com/photo-1465101178521-c1a9136a3b99?auto=format&fit=crop&w=1200&q=80');"></div>
      <div class="relative z-10 text-center">
        <h1 class="text-4xl md:text-6xl font-extrabold drop-shadow mb-2">Articles & News</h1>
        <p class="text-lg md:text-2xl font-medium drop-shadow">Stay updated with the latest articles and news.</p>
      </div>
    </section>

    <!-- Article List -->
    <div class="mw-3xl mx-auto mb-12">
       <ArticleList/>
    </div>
  </main>
</template>

<script setup>
</script>
