<template>
  <div class="flex items-center justify-center h-screen bg-gray-100">
    <div class="w-full max-w-md p-8 bg-white shadow-lg rounded-lg">
      <h2 class="text-2xl font-bold mb-4 text-center">Login</h2>
      <LoginForm />
    </div>
  </div>
</template>

<script setup>
import LoginForm from '../components/LoginForm.vue'
</script>
