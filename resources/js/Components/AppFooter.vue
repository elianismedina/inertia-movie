<script setup>
import AccordionPanel from '@/Components/AccordionPanel.vue';
</script>
<template>
    <footer class="w-full">
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
        <div class="bg-indigo-600 text-white py-2 w-full">
            <p class="ml-6 mb-4">Síguenos en:</p>
            <div class="flex flex-row items-center justify-center">
                <a href="#" class="ml-4">Facebook</a>
                <a href="#" class="ml-4">Twitter</a>
                <a href="#" class="ml-4">Instagram</a>
                <a href="#" class="ml-4">Youtube</a>
            </div>

        </div>
        <div class="grid grid-cols bg-slate-50 text-slate-900">
            <div class=" w-3/4 p-4 mx-auto">
                <p class="text-xs">Usar este sitio implica que usted acepta nuestros <span class="font-bold">Términos y
                        condiciones -
                        Políticas de privacidad</span> - Prohibida su reproducción total o parcial, así como su
                    traducción a
                    cualquier idioma sin autorización escrita de su titular Registrada en Colombia - Sur América -
                    Nit
                    901494862-1. Copyright 2024</p>
            </div>

        </div>
    </footer>
</template>
