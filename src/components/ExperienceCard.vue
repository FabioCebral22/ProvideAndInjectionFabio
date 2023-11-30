<template>
    <div class="card">
      <span class="card__text">
        {{ experience.name }}
      </span>
    </div>
  </template>
  
  <script setup lang="ts">
  import { defineProps } from 'vue';
  
  const props = defineProps(['experience']);
  </script>