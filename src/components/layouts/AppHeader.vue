<script setup>
import { ref } from "vue";
import { menuItems } from "../../data/header.ts";
import { Menu, X } from "lucide-vue-next";

const activeSection = ref("home");
const mobileMenuOpen = ref(false);

const setSection = (id) => {
  activeSection.value = id;
};
</script>
<template>
  <header class="relative z-50 glass-panel border-b-0 border-white/10 px-6 py-4 flex justify-between items-center bg-dark/80">
    <div class="flex items-center gap-2 cursor-pointer" @click="setSection('home')">
      <span class="font-bold text-lg tracking-wide block">Try<span class="text-cyan-400">Dev</span></span>
    </div>

    <nav class="hidden md:flex gap-1 bg-white/5 p-1 rounded-full border border-white/10">
      <button
        v-for="item in menuItems"
        :key="item.id"
        @click="setSection(item.id)"
        class="px-5 py-1.5 rounded-full text-sm font-medium transition-all duration-300 relative"
        :class="activeSection === item.id ? 'text-white' : 'text-gray-400 hover:text-white hover:bg-white/5'"
      >
        <span class="relative z-10">{{ item.label }}</span>
        <div
          v-if="activeSection === item.id"
          class="absolute inset-0 bg-white/10 rounded-full shadow-[inset_0_0_10px_rgba(255,255,255,0.1)] border border-white/10"
        ></div>
      </button>
    </nav>

    <div class="hidden md:flex items-center gap-4">
      <a href="#" class="text-gray-400 hover:text-cyan-400 transition-colors"><i data-lucide="aaaa" class="w-5 h-5"></i></a>
      <a href="#" class="text-gray-400 hover:text-cyan-400 transition-colors"><i data-lucide="linkedin" class="w-5 h-5"></i></a>
    </div>

    <button class="md:hidden text-gray-300 p-1" @click="mobileMenuOpen = !mobileMenuOpen">
      <X v-if="mobileMenuOpen" class="w-6 h-6" />
      <Menu v-else class="w-6 h-6" />
    </button>
  </header>

  <div
    v-if="mobileMenuOpen"
    class="md:hidden absolute top-17.5 left-0 w-full z-40 glass-panel border-b border-white/10 py-4 px-6 flex flex-col gap-2 bg-dark/95"
  >
    <button
      v-for="item in menuItems"
      :key="item.id"
      @click="
        setSection(item.id);
        mobileMenuOpen = false;
      "
      class="px-4 py-3 rounded-lg text-left text-sm font-medium transition-colors"
      :class="activeSection === item.id ? 'bg-cyan-500/10 text-cyan-400 border border-cyan-500/20' : 'text-gray-400 hover:bg-white/5 hover:text-white'"
    >
      {{ item.label }}
    </button>
  </div>
</template>
