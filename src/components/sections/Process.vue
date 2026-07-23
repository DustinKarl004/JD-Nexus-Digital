<script setup>
import { onMounted, onUnmounted, ref } from 'vue'

const terminalLines = [
  '$ jd-nexus discover',
  '✓ requirements gathered',
  '',
  '$ jd-nexus design',
  '✓ wireframes approved',
  '',
  '$ jd-nexus build --stage all',
  '✓ features shipped',
  '',
  '$ jd-nexus launch',
  '✓ live and supported 🚀',
]

const typedText = ref('')
let timer = null

function schedule(fn, delay) {
  timer = setTimeout(fn, delay)
}

onMounted(() => {
  const full = terminalLines.join('\n')
  let i = 0

  function typeTick() {
    i++
    typedText.value = full.slice(0, i)
    if (i >= full.length) {
      schedule(resetAndType, 2200)
      return
    }
    schedule(typeTick, 30)
  }

  function resetAndType() {
    i = 0
    typedText.value = ''
    schedule(typeTick, 400)
  }

  typeTick()
})

onUnmounted(() => clearTimeout(timer))

const steps = [
  {
    step: '01',
    title: 'Discover',
    description: 'We learn about your business, goals, and what the project needs to achieve.',
  },
  {
    step: '02',
    title: 'Design',
    description: 'We plan the structure and look of the product before writing any code.',
  },
  {
    step: '03',
    title: 'Build',
    description: "We develop the product in stages, keeping you updated along the way.",
  },
  {
    step: '04',
    title: 'Launch & Support',
    description: 'We ship the finished product and stay available for updates and fixes.',
  },
]
</script>

<template>
  <section id="process" class="scroll-mt-20 border-t border-slate-200 px-4 py-20 sm:px-6 dark:border-slate-700">
    <div class="mx-auto max-w-5xl">
      <div class="mb-12 text-center">
        <h2 class="text-3xl font-bold sm:text-4xl">How We Work</h2>
        <p class="mt-3 text-slate-600 dark:text-slate-300">
          A simple, transparent process from start to finish
        </p>
      </div>

      <div class="grid grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-4">
        <div
          v-for="item in steps"
          :key="item.step"
          class="flex flex-col items-center px-4 text-center sm:items-start sm:px-0 sm:text-left"
        >
          <span
            class="mb-3 flex size-10 items-center justify-center rounded-full bg-brand-blue text-sm font-bold text-white dark:bg-brand-yellow dark:text-slate-900"
          >
            {{ item.step }}
          </span>
          <h3 class="mb-2 text-lg font-semibold">{{ item.title }}</h3>
          <p class="text-sm text-slate-600 dark:text-slate-300">
            {{ item.description }}
          </p>
        </div>
      </div>

      <div
        class="mx-auto mt-12 w-full max-w-lg overflow-hidden rounded-xl border border-slate-200 bg-slate-100 text-left shadow-lg dark:border-slate-700 dark:bg-slate-900"
        aria-hidden="true"
      >
        <div class="flex items-center gap-1.5 border-b border-slate-200 px-4 py-2.5 dark:border-slate-700">
          <span class="size-2.5 rounded-full bg-red-500"></span>
          <span class="size-2.5 rounded-full bg-brand-yellow"></span>
          <span class="size-2.5 rounded-full bg-emerald-500"></span>
          <span class="ml-2 text-xs text-slate-500 dark:text-slate-400">process.sh</span>
        </div>
        <pre
          class="relative overflow-x-auto p-4 text-sm leading-relaxed text-slate-700 dark:text-slate-200"
        ><code class="invisible block" aria-hidden="true">{{ terminalLines.join('\n') }}</code><code class="absolute inset-0 p-4">{{ typedText }}<span class="typing-cursor text-brand-blue dark:text-brand-yellow">▌</span></code></pre>
      </div>
    </div>
  </section>
</template>

<style scoped>
.typing-cursor {
  animation: blink 1s step-end infinite;
}

@keyframes blink {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
}

@media (prefers-reduced-motion: reduce) {
  .typing-cursor {
    animation: none;
  }
}
</style>
