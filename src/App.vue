<script setup>
  import Formulario from './components/Formulario.vue';
  import ComprasRealizadas from './components/ComprasRealizadas.vue'
  import AlertasMensaje from './components/AlertasMensaje.vue';

  import { reactive, ref } from 'vue';

  const clientes = reactive({
    producto: '',
    precio: ''
  })

  const productos = ref([])

  //agregar producto
  const agregarProducto = () => {
    console.log(productos.value.target)
  }


</script>

<template>
  <div class = " flex w-screen min-h-screen">
     
      <Formulario
        v-model:producto="clientes.producto"
        v-model:precio="clientes.precio"
        @agregar-producto="agregarProducto"
      />

      <ComprasRealizadas 
        v-if="productos.length > 0"
      />

      <div class="bg-orange-500 w-1/2 container m-auto rounded-2xl">
        <div v-if="productos.values">
            <p class="text-xl p-5">No tienes ningun <span class="font-extrabold">producto</span></p>
        </div>
      </div>
    
  </div>
</template>




