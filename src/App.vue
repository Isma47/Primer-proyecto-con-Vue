<script setup>
  import Formulario from './components/Formulario.vue'
  import { reactive } from 'vue'

  const formulario = reactive({
        nombre: '',
        precio: ''
  })

</script>

<template>
  <main class="bg-slate-200 w-screen h-screen">
    <div class="container m-auto flex gap-4">
      <!-- Formulario de compras  -->
      <div class="w-1/2">
        <Formulario 
          v-model:nombre="formulario.nombre"
          v-model:precio="formulario.precio"
        />
      </div>

      <!-- Compras hechas -->
      <div
       class="w-1/2 shadow-md bg-orange-500 p-5 my-10 rounded-xl h-full ">
       <p v-if="formulario.precio === '' || formulario.nombre === ''">
          No hay productos
       </p>
      </div>
    </div>
  </main>
</template>

