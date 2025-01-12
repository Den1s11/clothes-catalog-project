<script setup>
  import { ref } from 'vue';

  const emit = defineEmits(['add-clothes']);
  
  const name = ref('');
  const image = ref('');
  const description = ref('');
  
  const addClothes = () => {
    if (name.value && image.value && description.value) {
      emit('add-clothes', { name: name.value, image: image.value, description: description.value });
    name.value = '';
    image.value = '';
    description.value = '';
    } else {
      alert("Please fill in all fields!");
    }
  };
  </script>

<template>
    <div class="p-6 bg-white rounded-lg shadow-lg max-w-md mx-auto">
    <h2 class="text-2xl font-bold text-gray-700 mb-4">Add New Clothes</h2>
    <form @submit.prevent="addClothes" class="space-y-4">
      <!-- Name Field -->
      <div>
        <label
          for="name"
          class="block text-sm font-medium text-gray-700 mb-1"
        >
          Name
        </label>
        <input
          id="name"
          v-model="name"
          type="text"
          placeholder="Enter clothes name"
          class="w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-green-600 focus:border-green-600"
        />
      </div>

      <!-- Image URL Field -->
      <div>
        <label
          for="image"
          class="block text-sm font-medium text-gray-700 mb-1"
        >
          Image URL
        </label>
        <input
          id="image"
          v-model="image"
          type="text"
          placeholder="Enter image URL"
          class="w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-green-600 focus:border-green-600"
        />
      </div>

      <!-- Description Field -->
      <div>
        <label
          for="description"
          class="block text-sm font-medium text-gray-700 mb-1"
        >
          Description
        </label>
        <textarea
          id="description"
          v-model="description"
          rows="3"
          placeholder="Enter clothes description"
          class="w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-green-600 focus:border-green-600 resize-none"
        ></textarea>
      </div>

      <!-- Submit Button -->
      <div>
        <button
          type="submit"
          class="w-full py-2 px-4 bg-green-600 text-white font-semibold rounded-md shadow-sm hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-green-600 focus:ring-offset-2"
        >
          Add Clothes
        </button>
      </div>
    </form>
  </div>
  </template>
  