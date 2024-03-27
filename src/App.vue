<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { useRoute } from 'vue-router'

const route = useRoute()
console.log(route.name)
</script>

<template>
  <div class="wrapper h-screen w-screen bg-zinc-100 text-gray-700">
    <div class="container mx-auto">
      <nav class="flex justify-center space-x-2 py-8">
        <RouterLink
          to="/"
          class="font-bold underline underline-offset-4 transition-colors duration-150 ease-in"
          active-class="text-teal-600"
          >Home</RouterLink
        >
        <span>|</span>
        <RouterLink
          to="/about"
          class="font-bold underline underline-offset-4 transition-colors duration-150 ease-in"
          active-class="text-teal-600"
          >About</RouterLink
        >
        <span>|</span>
        <RouterLink
          to="/content"
          class="font-bold underline underline-offset-4 transition-colors duration-150 ease-in"
          active-class="text-teal-600"
          >Content</RouterLink
        >
      </nav>
      <RouterView />
    </div>
  </div>
</template>

<style scoped></style>
