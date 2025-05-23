<template>
   <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
      <div v-for="item in relatedPostList?.data?.stories" :key="item.name" class="bg-white rounded shadow p-6 flex flex-col items-start">
        <h3 class="text-xl font-semibold mb-2">{{ item.name }}</h3>
        <p class="text-gray-600 mb-4">{{ item?.content?.page_description }}</p>
        <a class="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700" :href="'/'+item.full_slug" data-tag="read_article_click" v-bind:data-label="item.name">Read More</a>
      </div>
    </div>
</template>

<script setup>
const relatedPostList = await useStoryblokApi().get('cdn/stories', {
  version: 'draft',
  starts_with: 'resources-support/',
  excluding_slugs: 'resources-support/articles'
});
</script>
