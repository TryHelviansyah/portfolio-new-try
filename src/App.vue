<script setup>
import { ref } from "vue";
import BackgroundEffects from "./components/layouts/BackgroundEffects.vue";
import AppHeader from "./components/layouts/AppHeader.vue";
</script>

<style scoped></style>
<template>
  <div class="h-dvh w-full relative flex flex-col font-sans selection:bg-cyan-500/30 selection:text-white">
    <AppHeader />

    <BackgroundEffect />
  </div>
</template>
