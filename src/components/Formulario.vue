<script setup>
import { reactive } from 'vue';
import AlertasMensaje from './AlertasMensaje.vue';

const emit = defineEmits(['update:producto', 'update:precio', 'agregar-producto'])
const props = defineProps({
    producto: {
        type: String,
        required: true
    },
    precio: {
        type: String,
        required: true
    }
})

const errores = reactive({
    mensaje: '',
    tipo: ''
})

const mandarInfo = () => {
    if (props.producto === "" || props.precio === "") {
        errores.mensaje = 'Es obligatorio llenar todos los campos'
        errores.tipo = 'error'
        return
    } else {
        errores.mensaje = 'Enviado con exito'
    }
}



</script>


<template>
    <form 
        action=""
        class=" bg-orange-600 w-1/2 container m-auto rounded-2xl p-5 mx-10" 
        @submit.prevent="mandarInfo"
        @submit="$emit('agregar-producto')"
        >
        
        <AlertasMensaje :mensaje="errores.mensaje" :tipo="errores.tipo" v-if="errores.mensaje"/>

        <div class="flex flex-col mt-5">
            <label for="" class="text-lg font-semibold">
                Producto:</label>

            <input class="p-2 rounded-md" type="text" placeholder="Ingrese el producto"
                @input="$emit('update:producto', $event.target.value)">
        </div>


        <div class="flex flex-col mt-5">
            <label for="" class="text-lg font-semibold">
                Costo del producto:</label>


            <input class="p-2 rounded-md" type="text" placeholder="Ingrese el costo del producto"
                @input="$emit('update:precio', $event.target.value)">
        </div>

        <input type="submit" class="m-auto mt-9 rounded-2xl bg-white px-4 py-2 font-bold">
    </form>
</template>

