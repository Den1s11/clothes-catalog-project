  <script setup>
  const props = defineProps({
  id: String,
  name: String,
  image: String,
  description: String
  });

  const emit = defineEmits(['delete-clothes']);

  const deleteClothes = () => {
    console.log('Emitting delete-clothes for:', props.id);
    emit('delete-clothes', props.id);
  };
  </script>

<template>
     <div class="max-w-xs rounded-lg border border-gray-300 shadow-lg">
    <!-- Image Section -->
    <img :src="props.image" alt="Clothes Image" class="w-full h-48 object-cover rounded-t-lg">

    <!-- Content Section -->
    <div class="p-4">
      <!-- Clothes Name  -->
      <h2 class="text-xl font-bold mb-2">{{ props.name }}</h2>

      <!-- Clothes Description -->
      <p class="text-gray-700 text-sm mb-4">{{ props.description }}</p>

      <!-- Delete Button -->
      <button
        @click="deleteClothes"
        class="w-full py-2 bg-red-600 text-white rounded-md hover:bg-red-700 transition-colors"
      >
        Delete
      </button>
    </div>
  </div>
  </template>
  