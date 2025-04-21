<template>
    <div class="bg-white rounded-2xl shadow p-6 max-w-xl mx-auto">
        <h2 class="text-xl font-semibold mb-2">{{ aprendizaje.titulo }}</h2>
        <p class="text-gray-700 mb-4">{{ aprendizaje.contenido }}</p>
        <div class="flex justify-between items-center">
            <span class="text-sm text-indigo-500 uppercase font-semibold">{{ aprendizaje.categoria }}</span>

            <button
                @click="copiarAprendizaje"
                title="Copiar aprendizaje"
                class="text-sm text-gray-400 cursor-pointer hover:text-indigo-600 transition"
            >
                📋
            </button>
        </div>
    </div>
</template>

<script setup>
    import { toast } from 'vue-sonner'

    const props = defineProps({
        aprendizaje: Object
    })

    function copiarAprendizaje() {
        const texto = `🧠 ${props.aprendizaje.titulo}\n\n${props.aprendizaje.contenido} \n\n#AprendeYa`;
        navigator.clipboard.writeText(texto)
        .then(() => {
            toast.success('Copiado al portapapeles')
        })
        .catch(() => {
            toast.error('No se pudo copiar')
        });
    }
</script>