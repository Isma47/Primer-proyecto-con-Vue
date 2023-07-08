<script setup>
import {computed} from 'vue'
    const props = defineProps({
        mensaje: {
            type: String
        },
        tipo: {
            type: String
        }
    })

    const isError = computed(() => {
        return props.tipo;
    })
</script>

<template>
    <div 
    :class="[isError ? 'bg-red-500' : 'bg-green-500']"
    class="bg-red-500 p-2 font-bold">
       {{ props.mensaje }}
    </div>
</template>
