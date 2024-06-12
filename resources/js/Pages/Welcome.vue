<script setup>
import { Head, Link } from '@inertiajs/vue3';
import HomepageLayout from '@/Layouts/HomepageLayout.vue';
import Welcome from '@/Components/Welcome.vue';
import { ref } from 'vue';

const showingNavigationDropdown = ref(false);

</script>
<template>
    <HomepageLayout title="Welcome page">

        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Dashboard
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <Welcome v-if="!showingNavigationDropdown" />
                    <Welcome v-else />
                </div>
            </div>
        </div>
    </HomepageLayout>
</template>
