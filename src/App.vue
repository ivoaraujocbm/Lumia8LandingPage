<template>
  <div class="min-h-screen bg-slate-50 text-slate-900 font-sans selection:bg-blue-100 selection:text-blue-600">
    <Navbar />

    <Hero />

    <AppShowcase />

    <IALab />

    <section class="py-24 bg-white relative">
      <div class="container mx-auto px-6">
        <div class="bg-[#2563eb] rounded-[3rem] p-12 md:p-20 text-center relative overflow-hidden shadow-2xl shadow-blue-500/20">
          <div class="absolute top-0 right-0 w-64 h-64 bg-white/10 rounded-full -mr-20 -mt-20 blur-3xl opacity-50" />
          <div class="absolute bottom-0 left-0 w-96 h-96 bg-blue-400/20 rounded-full -ml-32 -mb-32 blur-[80px]" />
          
          <div class="relative z-10">
            <h2 class="text-3xl md:text-5xl font-black text-white mb-6 uppercase tracking-tighter">
              Transforme sua Operação Hoje
            </h2>
            <p class="text-blue-100 text-lg mb-10 max-w-2xl mx-auto font-light">
              Não fique para trás na corrida da inteligência artificial. Integre a Lumia 8 ao seu ecossistema e escale seu atendimento.
            </p>


            <div class="flex flex-col sm:flex-row gap-4 justify-center">
              <button class="px-12 py-5 bg-white text-[#2563eb] font-black rounded-2xl text-xl uppercase tracking-tighter hover:bg-slate-50 hover:scale-105 transition-all">
                Falar com Especialista
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <Footer />
  </div>
</template>

<script setup>
import AppShowcase from './components/AppShowcase.vue';
import Footer from './components/Footer.vue';
import Hero from './components/Hero.vue';
import IALab from './components/IALab.vue';
import Navbar from './components/Navbar.vue';

</script>
