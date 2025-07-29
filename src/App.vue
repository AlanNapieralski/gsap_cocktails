<script setup lang="ts">
import { ScrollTrigger, SplitText } from 'gsap/all'
import { gsap } from 'gsap'

gsap.registerPlugin(ScrollTrigger, SplitText)

</script>

<template>
  <div class="flex-center h-screen">
    <h1 class="text-3xl text-indigo-300">Hello, GSAP!</h1>
  </div>
</template>