<script setup>
import { reactive } from 'vue'

import LearningResource from '@/components/LearningResources/LearningResource.vue'

// Dummy data
const storedResources = reactive([
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
  <ul>
    <learning-resource
      v-for="resource in storedResources"
      :key="resource.id"
      :title="resource.title"
      :description="resource.description"
      :link="resource.link"
    ></learning-resource>
  </ul>
</template>

<style scoped></style>
