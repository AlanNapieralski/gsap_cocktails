<script setup lang="ts">
import { sliderLists as AllCocktails } from '../../constants'
import { ref, computed, watch } from 'vue'
import gsap from 'gsap'


const contentRef = ref(null)

const currentIndex = ref(0)

const isActive = (index: number) => index === currentIndex.value

const totalCocktails = AllCocktails.length

const goToSlide = (index: number) => {
    currentIndex.value = (index + totalCocktails) % totalCocktails
}

// Make these computed properties so they're reactive
const currentCocktail = computed(() => AllCocktails[currentIndex.value])
const prevCocktail = computed(() => AllCocktails[(currentIndex.value - 1 + totalCocktails) % totalCocktails])
const nextCocktail = computed(() => AllCocktails[(currentIndex.value + 1) % totalCocktails])

watch(currentIndex, () => {
    gsap.fromTo('#title', {
        opacity: 0,
    }, {
        opacity: 1,
        duration: 1,
    })
    gsap.fromTo('.cocktail_img', {
        opacity: 0,
        xPercent: -100,
    }, {
        xPercent: 0,
        opacity: 1,
        duration: 1,
        ease: 'power1.inOut'
    })
    gsap.fromTo('.details h2', {
        yPercent: 100,
        opacity: 0,
    }, {
        yPercent: 0,
        opacity: 1,
        duration: 1,
        ease: 'power1.inOut'
    })
    gsap.fromTo('.details p', {
        yPercent: 100,
        opacity: 0,
    }, {
        yPercent: 0,
        opacity: 1,
        duration: 1,
        ease: 'power1.inOut'
    })
})
</script>

<template>
    <section id="menu" aria-labelledby="menu-heading">
        <img src="/images/slider-left-leaf.png" alt="left-leaf" id="m-left-leaf"></img>
        <img src="/images/slider-right-leaf.png" alt="right-leaf" id="m-right-leaf"></img>

        <h2 id="menu-heading" class="sr-only">Cocktail Menu</h2>

        <nav class="cocktail-tabs" aria-label="Cocktail Navigation">
            <button 
                v-for="(cocktail, index) in AllCocktails" 
                :key="index" 
                :class="isActive(index) ? 'text-white border-white' : 'text-white/50 border-white/50'"
                @click="goToSlide(index)"
            >
                <a :href="`#${index}`" class="cocktail-tab" :aria-label="cocktail.name">
                    {{ cocktail.name }}
                </a>
            </button>
        </nav>

        <div class="content">
            <div class="arrows">
                <button class="text-left" @click="goToSlide(currentIndex - 1)">
                    <span>{{ prevCocktail.name }}</span>
                    <img src="/images/right-arrow.png" alt="right-arrow" aria-hidden="true">
                </button>
                <button class="text-left" @click="goToSlide(currentIndex + 1)">
                    <span>{{ nextCocktail.name }}</span>
                    <img src="/images/left-arrow.png" alt="left-arrow" aria-hidden="true">
                </button>
            </div>
            <div class="cocktail">
                <img :src="currentCocktail.image" alt="cocktail-image">
            </div>
            <div class="recipe">
                <div ref="contentRef" class="info">
                    <p>Recipe for:</p>
                    <p id="title">{{  currentCocktail.name }}</p>
                </div>
                <div class="details">
                    <h2>{{ currentCocktail.title }}</h2>
                    <p>{{ currentCocktail.description }}</p>
                </div>
            </div>
            
        </div>
    </section>
</template>