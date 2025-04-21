<template>
    <div class="p-4 min-h-screen bg-gradient-to-br from-indigo-100 to-white flex flex-col justify-center items-center">
        <Transition name="fade" mode="out-in">
            <AprendizajeCard v-if="aprendizaje" :key="aprendizaje.id" :aprendizaje="aprendizaje" />
        </Transition>
        <button
            @click="mostrarOtro"
            class="mt-6 bg-indigo-500 text-white px-4 py-2 rounded-xl cursor-pointer hover:bg-indigo-600"
        >
            🔄 Mostrar otro
        </button>
    </div>
</template>

<script setup>
    import { ref, onMounted } from 'vue'
    import AprendizajeCard from '../components/AprendizajeCard.vue'
    import aprendizajesData from '../data/aprendizajes.json'
    
    const aprendizaje = ref(null)
    
    function mostrarOtro() {
        const aleatorio = aprendizajesData[Math.floor(Math.random() * aprendizajesData.length)]
        aprendizaje.value = aleatorio
    }
    
    onMounted(() => {
        mostrarOtro()
    })
</script>

<style scoped>
.fade-enter-active, .fade-leave-active {
    transition: opacity 0.3s ease;
}
.fade-enter-from, .fade-leave-to {
    opacity: 0;
}
</style>