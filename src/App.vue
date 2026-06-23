<script setup>
import { ref } from "vue";
import BackgroundEffects from "./components/layouts/BackgroundEffects.vue";
import AppHeader from "./components/layouts/AppHeader.vue";
import HomeSection from "./sections/HomeSection.vue";

const activeSection = ref("home");
</script>

<style scoped></style>
<template>
  <div class="h-dvh w-full relative flex flex-col font-sans selection:bg-cyan-500/30 selection:text-white">
    <AppHeader />

    <div class="relative z-10 grow overflow-hidden flex items-center justify-center p-4 md:p-4">
      <HomeSection v-if="activeSection === 'home'" />
    </div>

    <BackgroundEffects />
  </div>
</template>
