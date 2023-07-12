<script setup lang="ts">
  import { ref, computed } from 'vue'
  import { defineComponent } from 'vue'
  import Home from '../pages/Home.vue'
  import About from '../pages/About.vue'
  import NotFound from '../pages/NotFound.vue'

  const routes = {
    '/': Home,
    'about': About
  }

  const currentPath = ref(window.location.hash)

  window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
  })

  const currentView = computed(() => {
  return (routes as { [key: string]: Component}) [currentPath.value.slice(1) || '/'] || NotFound
  })
</script>

<template>
  <div class="flex justify-evenly text-white bg-black p-4">
    <a href="/">Home</a>
    <a href="/about">About</a>
    <a href="">Skills</a>
    <a href="">Work</a>
    <a href="">Contact</a>
  </div>
</template>

<style scoped>
</style>

<!-- sample vue component
<script setup lang="ts">

</script>

<template>
  <div class="">
  </div>
</template>

<style scoped>
</style> -->
