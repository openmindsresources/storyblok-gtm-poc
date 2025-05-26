<template>
  <main class="min-h-screen flex flex-col bg-white">
    <!-- Hero Banner -->
    <section class="relative flex items-center justify-center h-64 md:h-96 bg-blue-600 text-white mb-12">
      <div class="absolute inset-0 bg-cover bg-center opacity-30" style="background-image: url('https://images.unsplash.com/photo-1465101046530-73398c7f28ca?auto=format&fit=crop&w=1200&q=80');"></div>
      <div class="relative z-10 text-center">
        <h1 class="text-4xl md:text-6xl font-extrabold drop-shadow mb-2">Contact Us</h1>
        <p class="text-lg md:text-2xl font-medium drop-shadow">We'd love to hear from you. Reach out with your questions or project ideas.</p>
      </div>
    </section>

    <!-- Contact Form -->
    <section class="max-w-2xl mx-auto px-4 mb-12">
      <h2 class="text-2xl font-bold mb-4 text-blue-700">Send Us a Message</h2>
      <form name="Contact Us" class="bg-white rounded shadow p-8 flex flex-col gap-4">
        <input type="text" placeholder="Name" class="border p-2 rounded" />
        <input type="email" placeholder="Email" class="border p-2 rounded" />
        <textarea placeholder="Message" class="border p-2 rounded"></textarea>
        <button type="submit" class="bg-blue-600 text-white px-6 py-2 rounded hover:bg-blue-700" data-form_name="Contact Us" data-tag="contact_submit">Send Message</button>
      </form>
    </section>

    <!-- Contact Information -->
    <section class="max-w-2xl mx-auto px-4 mb-12">
      <h2 class="text-2xl font-bold mb-4 text-blue-700">Contact Information</h2>
      <div class="bg-gray-50 rounded shadow p-6">
        <p class="mb-2"><span class="font-semibold">Address:</span> 123 Main Street, City, Country</p>
        <p class="mb-2"><span class="font-semibold">Phone:</span> +1 234 567 890</p>
        <p><span class="font-semibold">Email:</span> info@dummycorporate.com</p>
      </div>
    </section>

    <!-- Map -->
    <section class="max-w-2xl mx-auto px-4 mb-12">
      <h2 class="text-2xl font-bold mb-4 text-blue-700">Our Location</h2>
      <div class="w-full h-64 rounded overflow-hidden shadow">
        <iframe class="w-full h-full" frameborder="0" style="border:0" src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3151.835434509374!2d144.9537363153169!3d-37.816279779751554!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x6ad65d43f1f1f1f1%3A0x5045675218ce6e0!2sDummy%20Location!5e0!3m2!1sen!2sau!4v1610000000000!5m2!1sen!2sau" allowfullscreen></iframe>
      </div>
    </section>
  </main>
</template>

<script setup>
</script>
