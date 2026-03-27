<script setup>
import { ref, onMounted } from 'vue'

import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import Services from './components/Services.vue'
import AboutCompany from './components/AboutCompany.vue'
import About from './components/About.vue'
import SpecialOffers from './components/SpecialOffers.vue'
import Testimonial from './components/Testimonial.vue'
import Cta from './components/Cta.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'
import FloatingButton from './components/FloatingButton.vue'

</script>

<template>
    <Header />
    <Hero />
    <AboutCompany />
    <Services /> 
    <About />
    <SpecialOffers />
    <Testimonial />
    <Cta />
    <Contact />
    <Footer />
    <FloatingButton />
</template>
