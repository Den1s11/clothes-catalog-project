<script setup>
import { ref, computed, onMounted } from 'vue';
import AddClothes from '@/components/AddClothes.vue';
import axios from 'axios';

const addClothes = async (newClothes) => {
  try {
    const response = await axios.post('http://localhost:5000/clothes', newClothes);
    console.log('Clothes added successfully:', response.data);
    alert('Clothes added successfully!');
  } catch (error) {
    console.error('Error adding clothes:', error);
    alert('Failed to add clothes. Please try again.');
  }
};
</script>

<template>
    <AddClothes @add-clothes="addClothes" />
</template>