<script setup>
import { Head, Link } from '@inertiajs/vue3';
import FrontendVue from '@/Layouts/Frontend.vue';
import Hero from '@/Components/Frontend/Hero.vue';
import Promote from '@/Components/Frontend/Promote.vue';
import About from '@/Components/Frontend/About.vue';
import Skills from '@/Components/Frontend/Skills.vue'
import Portfolio from '@/Components/Frontend/Portfolio.vue'
import Services from '@/Components/Frontend/Services.vue'
import ContactMe from '@/Components/Frontend/ContactMe.vue';

const props = defineProps({
    skills: Object,
    projects: Object
});

</script>

<template>
    <Head title="Welcome" />
    <FrontendVue>
        <!-- Hero -->
        <Hero/>
        <!-- Promote tail-100 -->
        <Promote/>
        <!-- About -->
        <About/>
        <!-- Skills -->
        <Skills :skills="skills" />
        <!-- Projects -->
        <Portfolio :projects="projects" :skills="skills"/>
        <!-- services -->
        <Services />
        <!-- ContactMe -->
        <ContactMe />
    </FrontendVue>
</template>

<style></style>
