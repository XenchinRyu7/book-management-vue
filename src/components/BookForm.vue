<template>
  <div>
    <h2 class="text-xl font-bold mb-4">Add/Edit Book</h2>
    <form @submit.prevent="submitForm" class="space-y-4">
      <div>
        <label for="title" class="block text-sm font-medium text-gray-700">Title</label>
        <input
          type="text"
          id="title"
          v-model="form.title"
          class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm"
          required
        />
      </div>
      <div>
        <label for="author" class="block text-sm font-medium text-gray-700">Author</label>
        <input
          type="text"
          id="author"
          v-model="form.author"
          class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm"
          required
        />
      </div>
      <button type="submit" class="py-2 px-4 bg-blue-600 text-white rounded-md hover:bg-blue-700">
        Save
      </button>
    </form>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
import axios from 'axios'

const props = defineProps({
  bookId: Number
})

const form = ref({
  title: '',
  author: ''
})
const editing = ref(false)

const submitForm = async () => {
  try {
    if (editing.value) {
      await axios.put(`http://localhost:8080/api/books/${props.bookId}`, form.value)
    } else {
      await axios.post('http://localhost:8080/api/books', form.value)
    }
    emit('book-added')
    resetForm()
  } catch (error) {
    console.error('Error saving book:', error)
  }
}

const resetForm = () => {
  form.value = { title: '', author: '' }
  editing.value = false
}

watch(
  () => props.bookId,
  async (newId) => {
    if (newId) {
      try {
        const response = await axios.get(`http://localhost:8080/api/books/${newId}`)
        form.value = response.data
        editing.value = true
      } catch (error) {
        console.error('Error fetching book for editing:', error)
      }
    }
  },
  { immediate: true }
)
</script>
