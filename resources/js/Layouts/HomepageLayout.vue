<script setup>
import { ref } from 'vue';
import { Head, Link, router } from '@inertiajs/vue3';
import ApplicationMark from '@/Components/ApplicationMark.vue';
import Banner from '@/Components/Banner.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
    title: {
        type: String,
        required: true,
    },
});
const showingNavigationDropdown = ref(false);

</script>
<template>
    <div>


        <Head :title="title" />
        <Banner />
        <div class="min-h-screen bg-gray-100">
            <nav class="bg-white border-b border-gray-100">
                <!-- Primary Navigation Menu -->
                <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                    <div class="flex justify-between h-16">
                        <div :class="{ 'hidden': showingNavigationDropdown }" class="flex items-center gap-4">
                            <!-- Logo -->
                            <div class="shrink-0 flex items-center">
                                <Link :href="route('dashboard')">
                                <ApplicationMark class="block h-9 w-auto" />
                                </Link>
                            </div>
                            <div class="space-x-8 sm:-my-px sm:ms-10 sm:flex">
                                <NavLink :href="route('login')"> Inicia sesión </NavLink>
                            </div>
                            <div class="space-x-8 sm:-my-px sm:ms-10 sm:flex">
                                <NavLink :href="route('register')"> Regístrate </NavLink>
                            </div>
                        </div>
                        <!-- Hamburger -->
                        <div class="-me-2 flex items-center sm:hidden">
                            <button
                                class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-gray-500 hover:bg-gray-100 focus:outline-none focus:bg-gray-100 focus:text-gray-500 transition duration-150 ease-in-out"
                                @click="showingNavigationDropdown = !showingNavigationDropdown">
                                <svg class="h-6 w-6" stroke="currentColor" fill="none" viewBox="0 0 24 24">
                                    <path
                                        :class="{ 'hidden': showingNavigationDropdown, 'inline-flex': !showingNavigationDropdown }"
                                        stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M4 6h16M4 12h16M4 18h16" />
                                    <path
                                        :class="{ 'hidden': !showingNavigationDropdown, 'inline-flex': showingNavigationDropdown }"
                                        stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M6 18L18 6M6 6l12 12" />
                                </svg>
                            </button>
                        </div>

                    </div>

                </div>
                <!-- Responsive Settings Options -->
                <div :class="{ 'block': showingNavigationDropdown, 'hidden': !showingNavigationDropdown }"
                    class="sm:hidden bg-indigo-600 p-4">
                    <div class="grid grid-flow-row gap-8 text-white justify-center">
                        <h2>Pedir mi credito ya</h2>
                        <h2>Requisitos</h2>
                        <h2>Registarme</h2>
                        <h2>¿Cómo pagar?</h2>
                        <h2>¿Cuánto cuesta?</h2>
                        <h2>Ayuda</h2>
                    </div>
                </div>
            </nav>
            <!-- Page Content -->
            <main>
                <slot />
            </main>
        </div>
    </div>
</template>
