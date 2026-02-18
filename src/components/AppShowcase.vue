<template>
  <section id="aplicativos" class="py-24 bg-white">
    <div class="container mx-auto px-6">

      <div class="text-center mb-16">
        <div class="flex justify-center mb-4">
          <LayoutGrid class="text-blue-600" :size="32"/>
        </div>
        <h2 class="text-3xl md:text-5xl text-slate-900 tracking-tighter uppercase mb-4">
          Módulos Inteligentes
        </h2>
        <p class="text-slate-500">
          Gerencie e configure os recursos da sua automação com facilidade.
        </p>
      </div>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 max-w-6xl mx-auto">
        <AppCard 
          v-for="module in modules"
          :key="module.title"
          :icon="module.icon"
          :title="module.title"
          :description="module.description"
          :badge="module.badge"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import { 
  LayoutGrid,
  MessageSquare,
  Zap,
  Paperclip,
  Terminal,
  Calendar,
  Mic,
  Bell,
  Image as ImageIcon, 
  Database
} from 'lucide-vue-next';
import AppCard from './AppCard.vue';

const modules = [
  {
    icon: MessageSquare,
    title: 'Q&A',
    description: 'Configure perguntas e respostas frequentes para treinar sua IA.'
  },
  {
    icon: Zap,
    title: 'Follow-up',
    description: 'Configure lembretes e acompanhamentos automáticos via WhatsApp.'
  },
  {
    icon: Paperclip,
    title: 'Anexos',
    description: 'Gerencie arquivos e documentos para consulta da sua IA.'
  },
  {
    icon: Terminal,
    title: 'Funções JS',
    description: 'Crie e gerencie funções JavaScript para lógicas complexas.'
  },
  {
    icon: Calendar,
    title: 'Agendas',
    description: 'Conecte agendas para agendamentos automáticos inteligentes.'
  },
  {
    icon: Mic,
    title: 'Envio de Áudio',
    description: 'Envie mensagens de áudio geradas por síntese de voz.'
  },
  {
    icon: Bell,
    title: 'Notificações',
    description: 'Configure notificações push e email em tempo real.',
    badge: 'Versão Pro'
  },
  {
    icon: ImageIcon,
    title: 'Interpretação',
    description: 'Análise e interprete imagens enviadas pelos clientes.'
  },
  {
    icon: Database,
    title: 'Pix Integração',
    description: 'Integre pagamentos via Pix diretamente na conversa.',
    badge: 'Versão Pro'
  }
]
</script>

