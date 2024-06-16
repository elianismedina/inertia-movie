<template>
    <div class="w-full flex flex-col sm:justify-center items-center pt-6 sm:pt-0 bg-slate-100 h-full">
        <div>
            <slot name="logo" />
        </div>

        <div class="w-full h-screen sm:h-full sm:max-w-md mt-6 px-6 bg-white shadow-md overflow-hidden sm:rounded-lg">
            <slot />
        </div>
    </div>
</template>
