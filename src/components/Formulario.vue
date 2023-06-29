<script setup>
import { reactive, defineEmits, computed } from 'vue';
const props = defineProps({
    nombre: {
        type: String,
        required: true
    },
    precio: {
        type: String,
        required: true
    }
})

    defineEmits(['update:nombre', 'update:precio'])


    const alerta = reactive({
        tipo: '',
        mensaje: ''
    })

    const validarFormulario = () => {
        if(Object.values(props).includes('')) {
            alerta.mensaje = 'Todos los campos son obligatorios'
            alerta.tipo = 'error'
            return;
        }
    }

</script>

<template>
    
    <form class="shadow-md bg-orange-500 p-5 my-10 rounded-xl h-full flex- flex-col" @submit.prevent="validarFormulario">
        <div class="flex flex-col mb-5">
            <label class="text-lg font-bold" for="">Nombre del producto:</label>
            <input 
            class="p-2 rounded-xl" type="text" placeholder="Ingrese el nombre del producto"
            @input="$emit('update:nombre', $event.target.value)"
            :value="nombre"
            >
        </div>

        <div class="flex flex-col">
            <label class="text-lg font-bold" for="">Precio del producto:</label>
            <input 
            class="p-2 rounded-xl" type="text" placeholder="Ingrese el precio del producto"
            @input="$emit('update:precio', $event.target.value)"  
            :value="precio"
            >
        </div>

        <input type="submit" value="Enviar" class="bg-white py-2 px-10 rounded-xl mt-8 text-lg font-bold">

    </form>
    <div class="bg-red-500 rounded-xl text-center">{{ alerta.mensaje }}</div>
</template>

