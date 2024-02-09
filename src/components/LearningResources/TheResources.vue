<script setup>
import { ref, computed, reactive, provide } from 'vue'

import StoredResources from './StoredResources.vue'
import AddLearningResource from './AddLearningResource.vue'

const selectedTab = ref('stored-resources')

const setSelectedTab = (tab) => {
  console.log('setSelectedTab', tab)
  selectedTab.value = tab
}

const tabComponent = computed(() => {
  return selectedTab.value === 'stored-resources' ? StoredResources : AddLearningResource
})

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

provide('resources', storedResourcesData)

const storedResourcesButtonMode = computed(() => {
  return selectedTab.value === 'stored-resources' ? null : 'flat'
})

const addResourcesButtonMode = computed(() => {
  return selectedTab.value === 'add-resources' ? null : 'flat'
})
</script>

<template>
  <base-card>
    <base-button :mode="storedResourcesButtonMode" @click="setSelectedTab('stored-resources')"
      >Stored Resources</base-button
    >
    <base-button :mode="addResourcesButtonMode" @click="setSelectedTab('add-resources')"
      >Add Resource</base-button
    >
  </base-card>
  <component :is="tabComponent"></component>
</template>
