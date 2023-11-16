<script setup>
import { Head, Link } from '@inertiajs/vue3';
import FrontendVue from '@/Layouts/Frontend.vue';
import Hero from '@/Components/Frontend/Hero.vue';
import Promote from '@/Components/Frontend/Promote.vue';
import About from '@/Components/Frontend/About.vue';
import Skills from '@/Components/Frontend/Skills.vue'

const props = defineProps({
    skills: Object
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
    </FrontendVue>
</template>

<style></style>
