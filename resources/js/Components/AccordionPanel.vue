<script setup>
import { ref } from 'vue';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import { faArrowRight } from '@fortawesome/free-solid-svg-icons';
import { faArrowUp } from '@fortawesome/free-solid-svg-icons';
const props = defineProps({
    title: { type: String, required: true },
    ariaTitle: { type: String, required: true }
});
const showPanel = ref(false);
const togglePanel = (event) => {
    showPanel.value = !showPanel.value;
}
</script>

<template>
    <div class="panel container shadow-sm bg-indigo-600 text-slate-50">
        <button :arial-controls="'accordion-content-' + ariaTitle" :id="'accordion-control-' + ariaTitle"
            @click.prevent="togglePanel" class="p-4 w-full font-semibold flex flex-row items-center justify-between">
            {{ title }}
            <span class="material-icons" v-if="showPanel">
                <FontAwesomeIcon :icon="faArrowUp" class="px-2" />
            </span>
            <span class="material-icons" v-else>
                <FontAwesomeIcon :icon="faArrowRight" class="px-2" />
            </span>
        </button>
        <div :aria-hidden="!showPanel" :id="'content-' + ariaTitle" class="p-4" v-if="showPanel">
            <slot></slot>
        </div>
    </div>
</template>
