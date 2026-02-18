<template>
  <nav class="fixed top-0 w-full z-50 bg-white/80 backdrop-blur-lg border-b border-gray-100 py-4">
    <div class="container mx-auto px-6 flex justify-between items-center">

      <!--Logo e nome da Marca-->
      <div class="flex items-center gap-2">
        <div class="w-9 h-9 bg-[#2563eb] rounded-xl flex items-center justify-center shadow-lg shadow-blue-500/20">
          <Bot :size="20" class="text-white" />
        </div>
        <span class="text-[#1e293b] font-black text-2xl tracking-tighter">
          LUMIA <span class="text-[#2563eb]">8</span>
        </span>
      </div>

      <div class="hidden md:flex items-center gap-8">
        <a
          v-for="item in menuItems"
          :key="item"
          :href="`#${item.toLowerCase()}`"
          class="text-sm text-gray-500 hover:text-[#2563eb] transition-colors font-semibold uppercase tracking-widest"
        >
          {{ item }}
        </a>

        <button class="px-6 py-2.5 rounded-full bg-[#2563eb] text-white text-sm font-bold hover:bg-blue-700 transition-all shadow-md shadow-blue-500/10">
          Acessar Painel
        </button>
      </div>
    </div>
  </nav>
</template>
<script setup>
import { Bot } from 'lucide-vue-next';

const menuItems = ['Funcionalidade', 'Aplicativos', 'Laboratório']
</script>