
<template>
    <h1>Compra</h1>
    <ul>
        <li v-for="product in productos" :key="product.price">
            {{ product.name }} {{ product.price }} {{ monedaActual }} 
            <button @click="agregarAlCarrito(product)">Add to the cart</button>        </li>
    </ul>
</template>
<script setup lang="ts">
import { inject, ref, onMounted, defineEmits } from 'vue';
import type { Product } from './types';
const monedaActual = inject('monedaActual', ref(''));
const productosSeleccionados = ref([] as Product[]); 
onMounted(() => {
    console.log('Value of monedaActual:', monedaActual.value);
});



const agregarAlCarrito = (product: Product) => {
    const seleccion = [ product];
    productosSeleccionados.value.push(product);
    const nombres = productosSeleccionados.value.map(product => product.name);
    const nombresString = nombres.join(', ');
    alert('Productos seleccionados: ' + nombresString);

};

const productos = ref<Product[]>([
    { name: "Hamburger 🍔.", price: 5 },
    { name: "Cheeseburger 🧀", price: 6 },
    { name: "Impossible Burger 🥕", price: 7 },
    { name: "Fries 🍟", price: 2 }
]);
</script>