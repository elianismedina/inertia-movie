<script setup>
import AccordionPanel from '@/Components/AccordionPanel.vue';
</script>
<template>
    <footer>
        <AccordionPanel aria-title="contáctanos" title="Contáctanos">
            <div>
                <p>Información de contacto</p>
            </div>
        </AccordionPanel>
        <AccordionPanel aria-title="legales" title="Legales">
            <div>
                <p>Información legal</p>
            </div>
        </AccordionPanel>
        <AccordionPanel aria-title="informaciónutil" title="Información útil">
            <div>
                <p>Información útil</p>
            </div>
        </AccordionPanel>
    </footer>
</template>
