<template>
  <header class="bg-white shadow p-4 flex items-center justify-between w-full">
    <h1 class="text-xl font-bold">Dummy Corporate</h1>
    <nav class="space-x-4">
      <a href="/" class="text-blue-600 hover:underline" @click="trackNav('Home')">Home</a>
      <a href="/product-and-application" class="text-blue-600 hover:underline" @click="trackNav('Product & Application')">Product & Application</a>
      <a href="/project-inspiration" class="text-blue-600 hover:underline" @click="trackNav('Project Inspiration')">Project Inspiration</a>
      <a href="/resources-support/articles" class="text-blue-600 hover:underline" @click="trackNav('Articles')">Articles</a>
      <a href="/company" class="text-blue-600 hover:underline" @click="trackNav('Company')">Company</a>
      <a href="/about-us" class="text-blue-600 hover:underline" @click="trackNav('About Us')">About Us</a>
      <a href="/contact-us" class="text-blue-600 hover:underline" @click="trackNav('Contact Us')">Contact Us</a>
    </nav>
  </header>
</template>

<script setup>
function trackNav(label) {
  // Simulate analytics: navigation click
  // window.dataLayer.push({ event: 'nav_click', label })
}
</script>

<!--
Layout: layout-header.md
Analytics: nav clicks
-->
