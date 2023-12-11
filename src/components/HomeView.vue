<!-- HOMEVIEW.VUE -->
<template>
  <div class="container d-flex flex-column">
    <div class="d-flex centered m-3">
      <textarea class="custom-textarea" v-model="nombreComanda" readonly></textarea>
    </div>

    <div class="side-by-side">
      <input type="text" v-model="nombreRef">
      <button @click="actualizarNombre">Place Order</button>
    </div>

    <div class="d-flex m-3">
      <select id="moneda" v-model="monedaActual">
        <option v-for="moneda in monedas" :value="moneda" :key="moneda">
          {{ moneda }}
        </option>
      </select>
    </div>

    <div class="d-flex m3">
      <CalcularPrecio></CalcularPrecio>
    </div>
  </div>
</template>

<script setup lang="ts">
import CalcularPrecio from './CalcularPrecio.vue';
import { provide, ref } from 'vue';
import type { InjectionKey, Ref } from 'vue';

const nombreRef = ref('');
const nombreComanda = ref('');
const monedaActual = ref('$');

const monedas = ['$', '€', '£'];

provide('monedaActual', monedaActual);
const actualizarNombre = () => {
  nombreComanda.value = nombreRef.value;
}
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.centered {
  text-align: center;
}

.custom-textarea {
  border: 1px solid #ccc;
  padding: 5px;
  resize: none;
  width: 100%;
  box-sizing: border-box;
}

.side-by-side {
  display: flex;
  gap: 10px;
}
</style>
