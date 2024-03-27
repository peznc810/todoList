<script setup>
import { ref } from 'vue'
import gsap from 'gsap'
const items = ref(['phone', 'email', 'by post', 'by smoke signal'])

const beforeEnter = (el) => {
  el.style.transform = 'translateY(60px)'
  el.style.opacity = 0
}

const enter = (el, done) => {
  gsap.to(el, {
    duration: 1,
    y: 0,
    opacity: 0.8,
    onComplete: done,
    delay: el.dataset.index * 0.2,
  })
}
</script>

<template>
  <div class="content">
    <h2 class="mb-4 text-center text-xl font-bold">Content</h2>
    <TransitionGroup
      appear
      tag="ul"
      name="fade"
      class="mx-auto grid w-96 grid-cols-2 place-content-center gap-2"
      @before-enter="beforeEnter"
      @enter="enter"
    >
      <li
        v-for="(item, index) in items"
        :key="index"
        class="h-40 w-40 rounded-md text-center shadow-lg"
        :data-index="index"
      >
        {{ item }}
      </li>
    </TransitionGroup>
  </div>
</template>

<style scoped></style>
