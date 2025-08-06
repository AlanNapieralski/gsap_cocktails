<script setup lang="ts">
import { ScrollTrigger, SplitText } from 'gsap/all'
import { gsap } from 'gsap'
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import Cocktails from './components/Cocktails.vue'
import About from './components/About.vue'
import Art from './components/Art.vue'
import Menu from './components/Menu.vue'
import Contact from './components/Contact.vue'

gsap.registerPlugin(ScrollTrigger, SplitText)
</script>

<template>
<main>
    <Navbar />
    <Hero />
    <Cocktails />
    <About />
    <Art />
    <Menu />
    <Contact />
</main>
</template>