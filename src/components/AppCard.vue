<template>
  <div class="bg-white p-6 rounded-2xl border border-gray-100 shadow-sm hover:shadow-xl hover:-translate-y-1 transition-all group cursor-pointer">

    <div class="flex  justify-between items-start mb-4">

      <div class="w-12 h-12 rounded-xl bg-blue-50 flex items-center justify-center group-hover:bg-[#2563eb] transition-colors">
        <component :is="icon" class="text-[#2563eb] group-hover:text-white" :size="24"/>
      </div>

      <span
        v-if="badge"
        class="px-2 py-1 bg-amber-100 text-amber-700 text-[10px] font-bold rounded uppercase"
      >
        {{ badge }}
      </span>
    </div>

    <h4 class="text-lg font-bold text-gray-800 mb-2">{{ title }}</h4>

    <p class="text-gray-500 text-sm leading-relaxed">{{ description }}</p>

    <div class="mt-4 flex items-center text-blue-600 text-xs font-bold uppercase tracking-widest opacity-0 group-hover:opacity-100 transition-opacity">
      Configurar
      <ChevronRight :size="14"/>
    </div>
  </div>
</template>

<script setup>
import { ChevronRight } from 'lucide-vue-next';

const props = defineProps ({
  icon: {
    type: Object,
    required: true
  },
  title: {
    type: String,
    required: true
  },
  description: {
    type: String,
    required: true
  },
  badge: {
    type: String,
    default: null
  }
})
</script>