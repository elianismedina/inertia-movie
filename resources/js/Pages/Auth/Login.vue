<script setup>
import { Head, Link, useForm } from '@inertiajs/vue3';
import AuthenticationCard from '@/Components/AuthenticationCard.vue';
import AuthenticationCardLogo from '@/Components/AuthenticationCardLogo.vue';
import Checkbox from '@/Components/Checkbox.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import { faArrowRight } from '@fortawesome/free-solid-svg-icons';
defineProps({
    canResetPassword: Boolean,
    status: String,
});

const form = useForm({
    email: '',
    password: '',
    remember: false,
});

const submit = () => {
    form.transform(data => ({
        ...data,
        remember: form.remember ? 'on' : '',
    })).post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>

<template>

    <Head title="Inicia sesión" />
    <AuthenticationCard>
        <template #logo>
            <AuthenticationCardLogo />
            <div class="flex items-center justify-center">
                <h1 class="text-xl font-bold">Inicia sesión en Lineru</h1>
            </div>
        </template>
        <div class="w-full">
            <div v-if="status" class="mb-4 font-medium text-sm text-green-600">
                {{ status }}
            </div>
            <form @submit.prevent="submit" class="flex flex-col mt-6 mb-8 items-center justify-center">
                <div>
                    <InputLabel for="email" value="Email" />
                    <TextInput id="email" v-model="form.email" type="email" class="mt-1" required autofocus
                        autocomplete="email" />
                    <InputError class="mt-2" :message="form.errors.email" />
                </div>
                <div class="mt-4">
                    <InputLabel for="password" value="Password" />
                    <TextInput id="password" v-model="form.password" type="password" class="mt-1" required
                        autocomplete="current-password" />
                    <InputError class="mt-2" :message="form.errors.password" />
                </div>
                <div class="flex flex-col mt-8 gap-4">
                    <div>
                        <PrimaryButton class="flex justify-center" :class="{ 'opacity-25': form.processing }"
                            :disabled="form.processing">
                            Inicia sesión
                            <FontAwesomeIcon :icon="faArrowRight" class="px-2" />
                        </PrimaryButton>
                    </div>
                    <div class="mr-4">
                        <Link v-if="canResetPassword" :href="route('password.request')"
                            class="underline text-lg text-indigo-600 font-semibold hover:text-gray-900 rounded-md focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                        Olvidé mi contraseña
                        </Link>
                    </div>

                </div>
                <div class="flex flex-row mt-2 gap-4">
                    <div>
                        <p class="text-xs">¿No tienes cuenta?</p>
                    </div>
                    <Link :href="route('register')"
                        class="underline text-xs text-indigo-600 font-semibold hover:text-gray-900 rounded-md focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                    Regístrate
                    </Link>
                </div>
            </form>
        </div>

    </AuthenticationCard>
</template>
