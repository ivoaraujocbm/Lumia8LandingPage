<template>
    <section id="laboratório" class="py-24 bg-slate-900 text-white overflow-hidden relative">
        <div class="absolute inset-0 bg-[url('https://www.transparenttextures.com/patterns/carbon-fibre.png')] opacity-10" />

        <div class="container mx-auto px-6 relative z-10">
            <div class="flex flex-col lg:flex-row items-center gap-16">
                <div class="lg:w-1/2">
                    <h2 class="text-4xl md:text-6xl font-black mb-8 tracking-tighter uppercase leading-none">
                        Playground de <br/>
                        <span class="text-blue-500">Automação</span>
                    </h2>
                    <p class="text-slate-400 text-lg mb-8 leading-relaxed">
                        Teste o fluxo da sua automação em tempo real. Nossa engine processa lógicas complexas e integrações de forma instantânea através do núcleo Lumiá.
                    </p>

                    <div class="space-y-4">
                        <textarea
                            v-model="input"
                            class="w-full bg-black/50 border border-white/10 rounded-2xl p-6 text-sm outline-none focus:border-blue-500 transition-all h-32 resize-none"
                            placeholder="Ex: Como posso automatizar o suporte da minha software house?"
                        />

                        <button
                            @click="testIA"
                            :disabled="loading || !input"
                            class="w-full py-4 bg-blue-600 hover:bg-blue-500 rounded-xl font-bold flex items-center justify-center gap-2 transition-all disabled:opacity-50 disabled:cursor-not-allowed"
                        >
                            <Loader2 v-if="loading" class="animate-spin" :size="18" />
                            <Zap v-else :size="18" />

                            {{ loading ? 'Sincronizando módulos ...' : 'Simular no Lumia 8' }}
                        </button>
                    </div>
                </div>

                <div class="lg:w-1/2 w-full">
                    <div class="bg-black/40 border border-white/5 rounded-3xl p-8 min-h-[400px] flex flex-col shadow-2xl backdrop-blur-md">
                        <div class="flex items-center justify-between mb-6 border-b border-white/5 pb-4">
                            <div class="flex items-center gap-2">
                                <div class="w-3 h-3 rounded-full bg-red-500" />
                                <div class="w-3 h-3 rounded-full bg-amber-500" />
                                <div class="w-3 h-3 rounded-full bg-green-500" />
                            </div>
                            <span class="text-[10px] text-slate-500 font-bold tracking-widest uppercase">
                                Console de Diagnóstico v8.4
                            </span>
                        </div>

                        <div class="flex-grow text-slate-300 text-sm font-mono overflow-y-auto max-h-[300px] whitespace-pre-wrap leading-relaxed">
                            <div v-if="result" class="animate-fadeInUp">
                                {{ result }}
                            </div>
                            <span v-else class="opacity-50 italic">
                                > Aguardando comando para iniciar processamento...
                                > Workspace: CBM INFORMATICA carregado.
                                > Model: Gemini 2.5 Flash pronto.
                            </span>
                        </div>
                        <div class="mt-4 pt-4 border-t border-white/5 flex justify-between items-center text-[10px] text-slate-600 font-bold uppercase">
                            <span>Status: Pronto</span>
                            <span>Thread ID: {{ threadId }}</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { Loader2, Zap } from 'lucide-vue-next';
import { computed, ref } from 'vue';

const input = ref('')
const result = ref('')
const loading = ref(false)

const threadId = computed(() => {
    return Math.random().toString(36).substr(2, 9).toUpperCase()
})

const API_KEY = ""

/** 
 @param {string} prompt
 @param {string} systemInstruction
 @returns {Promise<string|null>}
*/

const callGemini = async (prompt, systemInstruction = "") => {
  try {
    const response = await fetch(
      `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${API_KEY}`,
      {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
          contents: [{ parts: [{ text: prompt }] }],
          
          systemInstruction: systemInstruction ? { parts: [{ text: systemInstruction }] } : undefined
        })
      }
    )

    if (response.ok) {
      const data = await response.json()
      return data.candidates?.[0]?.content?.parts?.[0]?.text
    }
    
    return null
  } catch (error) {
    console.error('Erro ao chamar Gemini:', error)
    return null
  }
}

const testIA = async () => {
  if (!input.value) return
  
  loading.value = true
  
  const systemPrompt = "Você é o sistema Lumia 8 da CBM Informática. Responda como um assistente de automação profissional. Ajude o usuário a entender como integrar IA no negócio dele de forma técnica e consultiva."
  
  const userPrompt = `Dada a demanda "${input.value}", como a Lumiá 8 resolveria isso usando seus módulos (Q&A, Agendas, Funções, etc)?`
  
  const response = await callGemini(userPrompt, systemPrompt)
  
  result.value = response || "Erro ao processar consulta."
  
  loading.value = false
}

</script>