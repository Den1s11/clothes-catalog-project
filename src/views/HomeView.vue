<script setup>
import { ref, computed, onMounted } from 'vue';
import ClothesFilter from '@/components/ClothesFilter.vue';
import ClothesList from '@/components/ClothesList.vue';
import axios from 'axios';

const clothes = ref([]);

onMounted(async () => {
  try {
    const response = await axios.get('http://localhost:5000/clothes');
    clothes.value = response.data;
  } catch (error) {
    console.error('Error fetching clothes', error);
  }
});

const filter = ref('');

const deleteClothes = async (id) => {
  if (!id) {
    console.error('ID is undefined! Cannot delete clothes.');
    return;
  }

  try {
    await axios.delete(`http://localhost:5000/clothes/${id}`);
    console.log('Clothes deleted with ID:', id);
    clothes.value = clothes.value.filter((item) => item.id !== id);
  } catch (error) {
    console.error('Error deleting clothes:', error);
    alert('Failed to delete clothes. Please try again.');
  }
};

const updateFilter = (value) => {
  filter.value = value;
};

const filteredClothes = computed(() =>
  clothes.value.filter((item) =>
    item.name.toLowerCase().includes(filter.value.toLowerCase())
  )
);
</script>

<template>
  <div> 
    <ClothesFilter @filter-changed="updateFilter" />
    <ClothesList
      :clothesList="filteredClothes"
      @delete-clothes="deleteClothes"
    />
  </div>
</template>