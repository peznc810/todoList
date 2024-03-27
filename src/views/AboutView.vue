<script setup>
import { Transition } from 'vue'
import gsap from 'gsap'

const beforeEnter = (el) => {
  el.style.transform = 'translateY(-60px)'
  el.style.opacity = 0
}

const afterEnter = (el) => {
  gsap.to(el, {
    duration: 1,
    y: 0,
    opacity: 1,
    ease: 'bounce.out',
  })
}
</script>

<template>
  <div class="about mx-auto w-3/4">
    <Transition name="fade" appear @before-enter="beforeEnter" @after-enter="afterEnter">
      <h2 class="mb-4 text-center text-xl font-bold">About</h2>
    </Transition>

    <p>
      嘗試看看用vue做出一個todoList，另外初嚐Tailwind
      css在製作動態效果、css布局以及bootstrap沒有的僞類，也認識了CLI和postcss之間使用上的差異。
      <br />
      <br />
      CLI可以自動生成Tailwind的CSS基礎架構，再去製作自定義的css。
      <br />

      Postcss則是一個工具集，可以轉換、擴展css，並透過config去製作自定義的css。
      <br />
      <br />
      另外，嘗試看看久聞的GSAP來製作動畫，目前只嘗試基礎的使用方式，未來將在人作品集網站上，練習更多動畫效果！
    </p>
  </div>
</template>

<style scoped></style>
