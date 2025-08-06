<script setup lang="ts">
import { openingHours } from '../../constants'
import { socials } from '../../constants'
import gsap from 'gsap'
import { onMounted } from 'vue'

onMounted(() => {
    const tl = gsap.timeline({
        scrollTrigger: {
            trigger: '#contact',
            start: 'top center',
        },
        ease: 'power1.inOut',
    })

    tl
    .from('#contact h2', {
        opacity: 0,
        yPercent: 100,
        duration: 0.8,
        ease: 'power1.inOut',
    })
    .from("#contact h3, #contact p", {
        opacity: 0,
        yPercent: 100,
        stagger: 0.2,
        ease: 'power1.inOut',
    })
})

</script>

<template>
    <footer id="contact">
        <div class="content">
            <h2>Where to Find Us</h2>

            <div>
                <h3>Visit Our Bar</h3>
                <p>456, Raq Blvd. #404, Los Angeles, CA 90210</p>
            </div>

            <div>
                <h3>Contact Us</h3>
                <p>+1 (234) 567-8900</p>
                <p>hello@jsmcocktail.com</p>
            </div>

            <div>
                <h3>Open Every Day</h3>
                <p v-for="time in openingHours" :key="time.day">
                    {{ time.day }} : {{ time.time }}
                </p>
            </div>

            <div>
                <h3>Socials</h3>

                <div class="flex-center gap-5">
                    <a v-for="social in socials" :href="social.url" :key="social.name" target="_blank" rel="noopener noreferrer" :aria-label="social.name">
                        <img :src="social.icon">
                    </a>
                </div>
            </div>
        </div>
    </footer>
</template>