<script setup>
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <!-- Header -->
    <Header />
    <main class="flex-grow container mx-auto my-8">
      <h1 class="text-3xl font-bold mb-4">Dashboard</h1>
      <router-link to="/books" class="text-blue-600 hover:underline">Manage Books</router-link>
    </main>
    <Footer />
  </div>
</template>
