<script setup>
import { ref } from 'vue';
import { Head, Link, router } from '@inertiajs/vue3';
import ApplicationMark from '@/Components/ApplicationMark.vue';
import Banner from '@/Components/Banner.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';
import AppFooter from '../Components/AppFooter.vue';
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
                    <div class="h-16">
                        <div :class="{ 'hidden': showingNavigationDropdown }"
                            class="flex flex-row justify-between gap-6">
                            <!-- Logo -->
                            <div class="shrink-0 flex items-center mt-2">
                                <Link :href="route('dashboard')">
                                <ApplicationMark class="block h-9 w-auto" />
                                </Link>
                            </div>

                            <!-- Navigation Links -->
                            <div class="space-x-8 sm:-my-px sm:ms-10 sm:flex mt-4">
                                <NavLink :href="route('login')" :active="route().current('dashboard')">
                                    Incia sesión
                                </NavLink>
                            </div>
                            <div class="space-x-8 sm:-my-px sm:ms-10 sm:flex mt-4">
                                <NavLink :href="route('register')" :active="route().current('dashboard')">
                                    Regístrate
                                </NavLink>
                            </div>
                            <!-- Hamburger -->
                            <div class=" mt-2 sm:hidden">
                                <button
                                    class="inline-flex items-center justify-center p-2 rounded-md text-black hover:text-gray-500 hover:bg-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-500 transition duration-150 ease-in-out"
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

                </div>
                <div :class="{ 'block': showingNavigationDropdown, 'hidden': !showingNavigationDropdown }"
                    class="sm:hidden">
                    <!-- Responsive Settings Options -->
                    <div class="pt-4 pb-1 border-t border-gray-200">
                        <div class="mt-3 space-y-1">
                            <div class="ml-4">Options</div>
                        </div>
                    </div>
                </div>
            </nav>
            <!-- Page Content -->
            <main>
                <slot />
            </main>
        </div>
        <AppFooter />
    </div>
</template>
