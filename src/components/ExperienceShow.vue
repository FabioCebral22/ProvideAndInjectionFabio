<template>
    <section>
      <h1>{{ experience.name }}</h1>
      <p>{{ experience.description }}</p>
    </section>
  </template>
  
  <script setup lang="ts">
  import { ref, computed, onMounted } from 'vue';
  import sourceData from '@/data.json';
  
  const props = defineProps(['id', 'experienceSlug']);
  
  const destination = ref(null);
  
  const experience = computed(() => {
    return destination.value?.experiences.find(
      (experience) => experience.slug === props.experienceSlug
    ) || {};
  });
  
  onMounted(() => {
    destination.value = sourceData.destinations.find(
      (destination) => destination.id === props.id
    );
  });
  </script>