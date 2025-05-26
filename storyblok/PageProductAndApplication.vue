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
      <form class="flex flex-wrap gap-4 justify-center mb-6">
        <select class="border rounded p-2" data-tag="product_filter_use" data-label="All Types" name="product_type">
          <option>All Types</option>
          <option>Type A</option>
          <option>Type B</option>
        </select>
        <select class="border rounded p-2" data-tag="product_filter_use" data-label="All Applications" name="application">
          <option>Application X</option>
          <option>Application Y</option>
        </select>
      </form>
    </section>

    <!-- setup:productList -->
    <section class="max-w-4xl mx-auto px-4 mb-12">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <div v-for="item in productList?.data?.stories" :key="item.id" class="bg-white rounded shadow p-6 flex flex-col items-center">
          <span class="text-lg font-semibold mb-2">{{ item.name }}</span>
          <a class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700" 
            :href="'/'+item.full_slug" 
            data-tag="view_product_click" 
            v-bind:data-value="item.name">View Product</a>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
const productList = await useStoryblokApi().get('cdn/stories', {
  "starts_with": "products",
})
</script>
