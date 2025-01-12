 <script setup>
  import ClothesCard from './ClothesCard.vue';
  
  const props = defineProps(['clothesList']);
  const emit = defineEmits(['delete-clothes']);
  
  </script>

<template>
    <section class="bg-blue-50 px-4 py-10">
      <div class="container-xl lg:container m-auto">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <ClothesCard
        v-for="(clothes, index) in clothesList"
        :key="index"
        :id="clothes.id"
        :name="clothes.name"
        :image="clothes.image"
        :description="clothes.description"
        @delete-clothes="(id) => { console.log('Received delete-clothes:', id); $emit('delete-clothes', id); }"
      />
        </div>
      </div>
    </section>
  </template>
  