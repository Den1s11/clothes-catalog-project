<script setup>
import { defineProps } from 'vue';
import { RouterLink, useRoute } from 'vue-router';

const isActiveLink = (routePath) => {
  const route = useRoute();
  return route.path === routePath;
}

defineProps({
  title: {
    type: String,
    default: 'Interactive Clothes Catalog Manager',
  },
});
</script>

<template>
       <nav class="bg-green-700 border-b border-green-500">
      <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
        <div class="flex h-20 items-center justify-between">
          <div
            class="flex flex-1 items-center justify-center md:items-stretch md:justify-start"
          >
          <header class="text-white font-bold text-xl">
          <h1>{{ title }}</h1>
          </header>
            <div class="md:ml-auto">
              <div class="flex space-x-2">
                <RouterLink
                  to="/"
                  :class="[
                    isActiveLink('/')
                    ? 'bg-green-900'
                    : 'hover:bg-gray-900 hover:text-white', 
                    'text-white', 'px-3', 'py-2', 'rounded-md',]"
                  >Home</RouterLink
                >
                <RouterLink
                  to="/clothes/add"
                  :class="[
                    isActiveLink('/clothes/add')
                    ? 'bg-green-900'
                    : 'hover:bg-gray-900 hover:text-white', 
                    'text-white', 'px-3', 'py-2', 'rounded-md',]"
                  >Add Clothes</RouterLink
                >
              </div>
            </div>
          </div>
        </div>
      </div>
    </nav>
</template>