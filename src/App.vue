<template>
  <body>
    <div class="container"> <router-view></router-view>
    </div>
  </body>
</template>
  
<script setup lang="ts">
import { useRouter } from 'vue-router';
const router = useRouter();
</script>
