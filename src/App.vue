<script setup>
import { reactive } from 'vue'

import StoredResources from '@/components/LearningResources/StoredResources.vue'
import TheHeader from '@/components/Layouts/TheHeader.vue'

// Dummy data
const storedResourcesData = reactive([
  {
    id: 1,
    title: 'Official Guide',
    description: 'The official Vue.js documentation',
    link: 'https://vuejs.org/',
  },
  {
    id: 2,
    title: 'Google',
    description: 'Learn to google...',
    link: 'https://www.google.com/',
  },
])
</script>

<template>
  <the-header title="Lifetime Learning Center"></the-header>
  <stored-resources :resources="storedResourcesData"></stored-resources>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
