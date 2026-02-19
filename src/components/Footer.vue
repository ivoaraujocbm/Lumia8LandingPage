<template>
    <footer class="bg-white py-16 border-t border-slate-100">
        <div class="container mx-auto px-6">

            <div class="grid grid-cols-1 md:grid-cols-4 gap-12 mb-12">
                <div class="col-span-1 md:col-span-2">
                    <div class="flex items-center gap-2 mb-6">
                        <div class="w-8 h-8 bg-blue-600 rounded-lg flex items-center justify-center shadow-lg shadow-blue-500/20">
                            <Bot class="text-white" :size="16" />
                        </div>
                        <span class="text-slate-900 font-black text-xl tracking-tight uppercase">
                            Lumia <span class="text-blue-600">8</span>
                        </span>
                    </div>
                    <p class="text-slate-500 max-w-sm text-sm leading-relaxed">
                        Plataforma avançada de orquestração de IA da CBM Informática. Desenvolvida para escalar operações complexas com inteligência real.
                    </p>
                </div>

                <div>
                    <h4 class="text-slate-900 font-bold mb-6 uppercase tracking-widest text-xs">
                        Produto
                    </h4>
                    <ul class="space-y-4 text-xs font-bold text-slate-400 uppercase tracking-widest">
                        <li
                            v-for="link in productLinks"
                            :key="link"
                            lass="hover:text-blue-600 cursor-pointer transition-colors"
                        >
                            {{ link }}
                        </li>
                    </ul>
                </div>

                <div>
                    <h4 class="text-slate-900 font-bold mb-6 uppercase tracking-widest text-xs">
                        Empresa
                    </h4>
                    <ul class="space-y-4 text-xs font-bold text-slate-400 uppercase tracking-widest">
                        <li 
                            v-for="link in companyLinks" 
                            :key="link"
                            class="hover:text-blue-600 cursor-pointer transition-colors"
                        >
                            {{ link }}
                        </li>
                    </ul>
                </div>
            </div>
            <div class="pt-8 border-t border-slate-100 flex flex-col md:flex-row justify-between items-center gap-4">
                <p class="text-[10px] text-slate-400 font-bold uppercase tracking-widest">
                    © 2026 LUMIA 8 PROJECT
                </p>

                <div class="flex gap-4">
                    <div class="w-6 h-6 bg-slate-100 rounded-full hover:bg-slate-200 transition-colors cursor-pointer" />
                    <div class="w-6 h-6 bg-slate-100 rounded-full hover:bg-slate-200 transition-colors cursor-pointer" />
                </div>
            </div>
        </div>
    </footer>
</template>

<script setup>
import { Bot } from 'lucide-vue-next';

const productLinks = ['Funcionalidades', 'API Docs', 'Status']
const companyLinks = ['CBM Informática', 'Privacidade', 'Contato']
</script>