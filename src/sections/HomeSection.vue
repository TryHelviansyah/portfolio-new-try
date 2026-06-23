<script setup>
import { ref, computed, onMounted } from "vue";

const typedCodeText = ref("");
const codeSnippet = `<?php

namespace App\\Http\\Controllers;

use Illuminate\\Http\\Request;

class PortfolioController extends Controller
{
    public function index()
    {
        return response()->json([
            'name' => 'Mujib',
            'role' => 'Full Stack Developer',
            'framework' => 'Laravel',
            'frontend' => 'Vue 3',
            'status' => 'Available'
        ]);
    }
}`;

let i = 0;
const typeCode = () => {
  if (i < codeSnippet.length) {
    typedCodeText.value += codeSnippet.charAt(i);
    i++;
    setTimeout(typeCode, Math.random() * 15 + 10);
  }
};

const highlightedCode = computed(() => {
  let html = typedCodeText.value
    .replace(/&/g, "&amp;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;")
    .replace(/(namespace|use|class|extends|public|function|return)/g, '<span class="kw">$1</span>')
    .replace(/(App\\Http\\Controllers|Illuminate\\Http\\Request|Controller)/g, '<span class="func">$1</span>')
    .replace(/('[^']*')/g, '<span class="str">$1</span>')
    .replace(/(\$[\w]+)/g, '<span class="var">$1</span>');
  return html;
});

onMounted(() => {
  typeCode();
});
</script>

<template>
  <section class="w-full h-full flex items-center justify-center">
    <div class="w-full max-w-7xl px-4 md:px-8 grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
      <div class="space-y-6 w-full text-center md:text-left flex flex-col items-center md:items-start">
        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full glass-panel border-white/10 text-cyan-400 text-sm mb-2 bg-white/5"></div>

        <h1 class="text-4xl sm:text-5xl lg:text-6xl font-extrabold tracking-tight leading-none flex flex-col gap-3">
          <span class="text-base sm:text-lg font-mono text-cyan-400/90 tracking-widest uppercase animate-pulse"> [ Hello World, I am ] </span>

          <span class="text-transparent bg-clip-text bg-linear-to-r from-cyan-400 via-sky-400 to-purple-500 drop-shadow-[0_0_20px_rgba(6,182,212,0.15)]">
            Try Helviansyah
          </span>

          <span class="text-xl sm:text-2xl lg:text-3xl text-gray-400 font-medium tracking-wide mt-1">
            ERP Support <span class="text-purple-400/80 font-mono">&amp;</span> <span class="text-white border-b-2 border-cyan-500/30 pb-1">Web Developer</span>
          </span>
        </h1>

        <p class="text-gray-400 text-base md:text-lg max-w-lg leading-relaxed">
          Building scalable web applications with Laravel, PHP, Vue, Python, and modern cloud technologies. Turning complex problems into elegant solutions.
        </p>

        <div class="flex flex-wrap justify-center md:justify-start gap-4 pt-2">
          <button
            class="px-6 py-3 rounded-lg bg-cyan-500 text-black font-medium hover:bg-cyan-400 hover:shadow-[0_0_20px_rgba(6,182,212,0.4)] transition-all duration-300 flex items-center gap-2 cursor-pointer"
          >
            View Projects
          </button>
          <button
            class="px-6 py-3 rounded-lg glass-panel bg-white/5 border border-white/10 hover:bg-white/10 hover:border-white/20 transition-all duration-300 flex items-center gap-2 text-white cursor-pointer"
          >
            Contact Me
          </button>
        </div>
      </div>

      <div class="relative group hidden md:block w-full">
        <div
          class="absolute -inset-1 bg-linear-to-r from-cyan-500 to-purple-500 rounded-xl blur opacity-25 group-hover:opacity-40 transition duration-1000"
        ></div>

        <div class="relative rounded-xl bg-[#1e1e1e] border border-gray-700/50 shadow-2xl overflow-hidden flex flex-col h-[400px]">
          <div class="bg-[#2d2d2d] px-4 py-3 flex items-center gap-2 border-b border-gray-700 select-none">
            <div class="w-3 h-3 rounded-full bg-red-500"></div>
            <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
            <div class="w-3 h-3 rounded-full bg-green-500"></div>
            <div class="mx-auto text-xs text-gray-400 font-mono">PortfolioController.php</div>
          </div>

          <div class="p-5 font-mono text-sm leading-relaxed text-gray-300 relative flex-grow pl-12 bg-[#1a1a1a] overflow-y-auto">
            <div
              class="absolute left-0 top-0 bottom-0 w-8 bg-[#151515] border-r border-gray-800/80 flex flex-col items-center py-5 text-gray-600 select-none text-xs gap-[1px]"
            >
              <span v-for="n in 26" :key="n">{{ n }}</span>
            </div>

            <pre class="whitespace-pre-wrap cursor-blink"><code v-html="highlightedCode"></code></pre>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
:deep(.kw) {
  color: #f472b6;
  font-weight: bold;
}
:deep(.func) {
  color: #60a5fa;
}
:deep(.str) {
  color: #34d399;
}
:deep(.var) {
  color: #fbbf24;
}

.cursor-blink::after {
  content: "┃";
  animation: blink 0.8s infinite step-end;
  color: #22d3ee;
}

@keyframes blink {
  80%,
  100% {
    opacity: 0;
  }
}
</style>
