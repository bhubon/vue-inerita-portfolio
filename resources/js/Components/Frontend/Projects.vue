<script setup>
import Project from './Project.vue';
import { ref } from 'vue';
const props = defineProps({
    skills: Object,
    projects: Object
})


const filteredProjects = ref(props.projects.data);

const selecteSkill = ref('all');

const filterProjects = (id) => {
    if (id == 'all') {
        filteredProjects.value = props.projects.data;
        selecteSkill.value = id;
    } else {
        filteredProjects.value = props.projects.data.filter(project => {
            return project.skill.id === id;
        });
        selecteSkill.value = id;
    }
}
</script>

<template>
    <div class="container mx-auto">
        <nav class="mb-12 border-b-2 border-light-tail-100 dark:text-dark-navy-100">
            <ul class="flex flex-col lg:flex-row justify-evenly items-center">
                <li class="cursor-pointer capitalize m-4">
                    <button @click="filterProjects('all')"
                        class="flex text-center px-4 py-2 hover:bg-accent text-white rounded-md" :class="[
                            selecteSkill == 'all' ? 'text-light-tail-500 dark:text-light-tail-500' : ''
                        ]">
                        All
                    </button>
                </li>
                <li class="cursor-pointer capitalize m-4" v-for="projectSkill in skills.data" :key="projectSkill.id">
                    <button @click="filterProjects(projectSkill.id)"
                        class="flex text-center px-4 py-2 hover:bg-accent text-white rounded-md" :class="[
                            selecteSkill == projectSkill.id ? 'text-light-tail-500 dark:text-light-tail-500' : ''
                        ]">
                        {{ projectSkill.name }}
                    </button>
                </li>
            </ul>
        </nav>
        <section class="grid gap-y-12 lg:grid-cols-3 lg:gap-8">
            <Project v-for="project in filteredProjects" :key="project.id" :project="project" />
        </section>
    </div>
</template>
  

<style scoped></style>