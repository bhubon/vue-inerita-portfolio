<script setup>
import { reactive } from 'vue'

import Checkbox from '@/Components/Checkbox.vue';
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { router } from '@inertiajs/vue3'

import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

const props = defineProps({
    skills: Array,
    project: Object
})

const form = useForm({
    name: props.project?.name,
    image: null,
    projectUrl: props.project?.project_url,
    skill_id: props.project?.skill_id,
})

const submit = () => {
    router.post(`/projects/${props.project.id}`, {
        _method: "put",
        name: form.name,
        image: form.image,
        projectUrl: form.projectUrl,
        skill_id: form.skill_id,
    });
}
</script>

<template>
    <Head title="Edit Project" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Edit Project</h2>
        </template>

        <div class="py-12">
            <div class="max-w-md mx-auto sm:px-6 lg:px-8 bg-white ">
                <form class="p-4" @submit.prevent="submit">
                    <div>
                        <InputLabel for="skill_id" value="Skill" />
                        <select id="skill_id" name="skill_id"
                            class="mt-1 block w-full pl-3 pr-10 text-base border-gray-300 focus:outline-none focus:ring-indigo-300 focus:border-indigo-300 rounded-md"
                            v-model="form.skill_id">
                            <option v-for="skill in skills" :key="skill.id" :value="skill.id">{{ skill.name }}</option>
                        </select>
                        <InputError class="mt-2" :message="$page.props.errors.skill_id" />
                    </div>
                    <div>
                        <InputLabel for="name" value="Name" />

                        <TextInput id="name" type="text" class="mt-1 block w-full" v-model="form.name" />

                        <InputError class="mt-2" :message="$page.props.errors.name" />
                    </div>
                    <div>
                        <InputLabel for="url" value="Url" />

                        <TextInput id="url" type="url" class="mt-1 block w-full" v-model="form.projectUrl" />

                        <InputError class="mt-2" :message="$page.props.errors.projectUrl" />
                    </div>
                    <div class="mt-2">
                        <InputLabel for="image" value="Image" />

                        <TextInput id="image" type="file" class="mt-1 block w-full"
                            @input="form.image = $event.target.files[0]" />

                        <InputError class="mt-2" :message="$page.props.errors.image" />
                    </div>

                    <div class="flex items-center justify-end mt-4">

                        <PrimaryButton class="ml-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                            Update
                        </PrimaryButton>
                    </div>
                </form>
            </div>
        </div>
    </AuthenticatedLayout>
</template>

<style scoped></style>