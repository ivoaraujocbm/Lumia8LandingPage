<template>
  <section class="relative pt-32 pb-20 overflow-hidden bg-slate-50">

    <div class="absolute top-0 left-0 w-full h-full opacity-40 pointer-events-none">
      <div class="absolute top-[-10%] left-[-10%] w-[40%] h-[40%] bg-blue-200 blur-[120px] rounded-full" />
      <div class="absolute bottom-[-10%] right-[-10%] w-[40%] h-[40%] bg-indigo-100 blur-[120px] rounded-full" />
    </div>

    <div class="container mx-auto px-6 relative z-10">

      <!--Conteúdo Princupal-->
      <div class="text-center max-w-4xl mx-auto">
        <div class="animate-fadeInUp">

          <span class="inline-block px-4 py-1.5 mb-6 text-xs font-bold tracking-widest text-blue-600 uppercase bg-blue-50 border border-blue-100 rounded-full">
            Plataforma de IA All-in-One
          </span>

          <h1 class="text-5xl md:text-7xl font-black text-slate-900 mb-8 tracking-tighter leading-[1.1]">
            A Inteligência que <br />
            <span class="text-transparent bg-clip-text bg-linear-to-r from-blue-600 to-indigo-600 italic">
              Impulsiona
            </span> seu Negócio.
          </h1>

          <p class="text-slate-600 text-lg md:text-xl max-w-2xl mx-auto mb-10 leading-relaxed font-light">
            Orquestre automações inteligentes, gerencie múltiplos workspaces e conecte seu ERP à potência da IA Generetiva com a tecnologia LUMIA8
          </p>

          <div class="flex flex-col sm:flex-row gap-4 justify-center mb-20">
            <button class="px-10 py-5 bg-[#2563eb] text-white font-black rounded-2xl hover:scale-105 transition-all shadow-2xl shadow-blue-500/30 text-lg">
              Criar Nova Automação
            </button>
            <button class="px-10 py-5 bg-white text-slate-700 font-bold border border-slate-200 rounded-2xl hover:bg-slate-50 transition-all text-lg">
              Ver Demonstração
            </button>
          </div>
        </div>
      </div>

      <div 
        class="relative max-w-6xl mx-auto bg-white rounded-[2.5rem] shadow-2xl border border-slate-200 overflow-hidden p-2 animate-fadeInUp"
        style="animation-delay: 0.3s"
      >
        <div class="bg-slate-50 rounded-4xl border border-slate-100 p-6 flex gap-4 min-h-125">

          <div class="w-16 md:w-56 hidden md:flex flex-col gap-4 border-r border-slate-200 pr-4">
            <div class="h-8 w-32 bg-slate-200 rounded mb-4" />

            <div
              v-for="(icon, index) in sidebarIcons"
              :key="index"
              :class="[
                'flex items-center gap-3 p-3 rounded-xl',
                index === 0 ? 'bg-blue-600 text-white shadow-lg' : 'text-slate-400'
              ]"
            >
              <component :is="icon" :size="20" />
              <span class="text-sm font-bold hidden md:block">Funcionalidades</span>
            </div>
          </div>

          <div class="grow p-4">
            <div class="flex justify-between items mb-8">
              <h3 class="text-2xl font-bold text-slate-800 tracking-tight">Automações Ativas</h3>
              <button class="bg-blue-600 text-white px-4 py-2 rounded-lg text-sm font-bold hover:bg-blue-700 transition-colors shadow-lg shadow-blue-500/20">
                + Nova
              </button>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
              <div
                v-for="(automation, index) in automations"
                :key="index"
                class="bg-white border border-slate-100 p-5 rounded-2xl flex items-center justify-between shadow-sm hover:border-blue-200 transition-colors group"
              >
                <div class="flex items-center gap-4">
                  <div
                    :class="[
                      'w-12 h-12 rounded-xl flex items-center justify-center font-bold text-white shadow-inner',
                      automation.color
                    ]"
                  >
                    {{ automation.name.charAt(0) }}
                  </div>

                  <div>
                    <div class="font-bold text-slate-800">{{ automation.name }}</div>
                    <div class="text-[10px] text-emerald-500 font-bold uppercase tracking-widest flex items-center gap-1">
                      <div class="w-1.5 h-1.5 bg-emerald-500 rounded-full animate-pulse" />
                      Ativa
                    </div>
                  </div>
                </div>

                <button class="text-blue-600 text-xs font-bold bg-blue-50 px-3 py-1.5 rounded-lg group-hover:bg-blue-600 group-hover:text-white transition-all">
                  ACESSAR
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { 
  Layout,
  Calendar,
  MessageSquare,
  Settings,
  Layers,
  Database

 } from 'lucide-vue-next';

const siderbarIcons = [
  Layout, 
  Calendar,
  MessageSquare,
  Settings,
  Layers,
  Database
 ]

 const automations = [
  { name: 'Lia (Oystr)', color: 'bg-emerald-500' },
  { name: 'Robeka Impact', color: 'bg-rose-500' },
  { name: 'Suporte Técnico CBM', color: 'bg-blue-500' },
  { name: 'Votorella', color: 'bg-orange-500' }
]

</script>