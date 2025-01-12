<script setup>
  import { ref } from 'vue';

  const emit = defineEmits(['filter-changed']);
  
  const filterValue = ref('');
  const updateFilter = () => {
    emit('filter-changed', filterValue.value);
  };
  </script>
  

<template>
     <div class="p-4 bg-gray-100 rounded-lg shadow-md">
    <label for="filter" class="block text-lg font-medium text-gray-700 mb-2">
      Filter Clothes by Name
    </label>
    <input
      id="filter"
      v-model="filterValue"
      @input="updateFilter"
      type="text"
      placeholder="Enter name..."
      class="w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-green-600 focus:border-green-600"
    />
  </div>
  </template>
  