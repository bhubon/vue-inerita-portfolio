<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link } from '@inertiajs/vue3';
defineProps({
    projects: Object
});
</script>

<template>
    <Head title="Projects" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Projects</h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="flex justify-end m-2 p-2">
                    <Link :href="route('projects.create')"
                        class="px-4 py-2 bg-indigo-500 hover:bg-indigo-700 text-white rounded-md">New Project</Link>
                </div>
                <div class="relative overflow-x-auto">
                    <div class="relative overflow-x-auto">
                        <table class="w-full text-sm text-left rtl:text-right text-gray-500 ">
                            <thead class="text-xs text-gray-700 uppercase bg-gray-50">
                                <tr>
                                    <th scope="col" class="px-6 py-3">
                                        ID
                                    </th>
                                    <th scope="col" class="px-6 py-3">
                                        Name
                                    </th>
                                    <th scope="col" class="px-6 py-3">
                                        Skill
                                    </th>
                                    <th scope="col" class="px-6 py-3">
                                        Image
                                    </th>
                                    <th scope="col" class="px-6 py-3">
                                        
                                    </th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="bg-white border-b" v-for="project in projects.data" :key="project.id">
                                    <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap ">
                                        {{ project.id }}
                                    </th>
                                    <td class="px-6 py-4">
                                        {{ project.name }}
                                    </td>
                                    <td class="px-6 py-4">
                                        {{ project.skill.name }}
                                    </td>
                                    <td class="px-6 py-4">
                                        <img :src="project.image" class="w-12 h-12 rounded-full" v-if="project.image !='' ">
                                    </td>
                                    <td>
                                        <Link :href="route('projects.edit',project.id)"
                                        class="font-medium text-blue-500 hove:text-blue-700 mr-2 "
                                         >Edit</Link>
                                        <Link method="delete" :href="route('projects.destroy',project.id)"
                                        as="button" type="button"
                                        class="font-medium text-red-500 hove:text-red-700 mr-2 "
                                         >Delete</Link>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>

                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>

<style scoped></style>