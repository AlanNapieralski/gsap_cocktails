<script setup lang="ts">
import { ScrollTrigger, SplitText } from 'gsap/all'
import { gsap } from 'gsap'
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'

gsap.registerPlugin(ScrollTrigger, SplitText)

</script>

<template>
<main>
    <Navbar />
    <Hero />
    <div class="h-dvh bg-black"></div>
</main>
</template>