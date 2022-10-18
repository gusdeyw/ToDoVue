<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div class="bg-[#f6ffff]">
    <div class="w-6/12 mx-auto bg-[#fff5d9] px-7 border-4 border-[#525252]">
      <RouterView />
    </div>
  </div>
</template>