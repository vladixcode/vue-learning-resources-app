<script setup>
import TheHeader from '@/components/Layouts/TheHeader.vue'
import TheResources from './components/LearningResources/TheResources.vue'
</script>

<template>
  <the-header title="Lifetime Learning Center"></the-header>
  <the-resources></the-resources>
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
