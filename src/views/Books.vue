<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'
import BookForm from '../components/BookForm.vue'
import BookList from '../components/BookList.vue'
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'

const books = ref([])

const fetchBooks = async () => {
  try {
    const response = await axios.get('http://localhost:8080/api/books')
    books.value = response.data
  } catch (error) {
    console.error('Error fetching books:', error)
  }
}

onMounted(fetchBooks)
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <Header />
    <main class="flex-grow container mx-auto my-8">
      <h1 class="text-3xl font-bold mb-4">Books</h1>
      <BookForm @book-added="fetchBooks" />
      <BookList :books="books" @book-edited="fetchBooks" />
    </main>
    <Footer />
  </div>
</template>
