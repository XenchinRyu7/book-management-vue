<template>
  <div>
    <table class="min-w-full divide-y divide-gray-200">
      <thead class="bg-gray-50">
        <tr>
          <th
            class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
          >
            Title
          </th>
          <th
            class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
          >
            Author
          </th>
          <th
            class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
          >
            Actions
          </th>
        </tr>
      </thead>
      <tbody class="bg-white divide-y divide-gray-200">
        <tr v-for="book in books" :key="book.id">
          <td class="px-6 py-4 whitespace-nowrap">{{ book.title }}</td>
          <td class="px-6 py-4 whitespace-nowrap">{{ book.author }}</td>
          <td class="px-6 py-4 whitespace-nowrap">
            <button @click="$emit('book-edited', book.id)" class="text-blue-600 hover:underline">
              Edit
            </button>
            <!-- Add delete button here if needed -->
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
const props = defineProps({
  books: Array
})
</script>
