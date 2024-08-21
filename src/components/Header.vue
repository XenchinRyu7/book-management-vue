<template>
  <header class="bg-blue-600 p-4 text-white">
    <div class="container mx-auto flex justify-between items-center">
      <img alt="Logo" src="@/assets/logo.svg" width="50" height="50" />

      <nav>
        <RouterLink to="/" class="mr-4 hover:underline">Home</RouterLink>
        <RouterLink to="/about" class="hover:underline">About</RouterLink>
      </nav>
    </div>
  </header>
</template>

<script setup>
import { RouterLink } from 'vue-router'
</script>
