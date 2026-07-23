<script setup>
import { onMounted, onUnmounted, ref } from 'vue'

const badgeText = 'Web & Software Development'
const typedBadge = ref('')
let badgeTimer = null

function scheduleBadge(fn, delay) {
  badgeTimer = setTimeout(fn, delay)
}

onMounted(() => {
  let i = 0

  function typeTick() {
    i++
    typedBadge.value = badgeText.slice(0, i)
    if (i >= badgeText.length) {
      scheduleBadge(resetAndType, 2000)
      return
    }
    scheduleBadge(typeTick, 55)
  }

  function resetAndType() {
    i = 0
    typedBadge.value = ''
    scheduleBadge(typeTick, 500)
  }

  typeTick()
})

onUnmounted(() => clearTimeout(badgeTimer))
</script>

<template>
  <section class="relative overflow-hidden px-4 py-20 sm:px-6 sm:py-32">
    <div
      class="pointer-events-none absolute inset-0 -z-10 bg-brand-blue/5 dark:bg-brand-blue/10"
    />

    <div class="mx-auto flex max-w-3xl flex-col items-center gap-6 text-center">
      <span
        class="inline-flex items-center gap-2 rounded-full border border-brand-blue/25 bg-brand-blue/5 px-4 py-1 text-sm font-medium text-brand-blue dark:border-brand-yellow/30 dark:bg-brand-yellow/10 dark:text-brand-yellow"
      >
        <span class="size-1.5 shrink-0 rounded-full bg-brand-yellow"></span>
        <span class="relative">
          <span class="invisible whitespace-nowrap" aria-hidden="true">{{ badgeText }}</span>
          <span class="absolute inset-0 whitespace-nowrap">{{ typedBadge }}<span class="badge-cursor">▌</span></span>
        </span>
      </span>

      <h1 class="text-4xl font-bold tracking-tight sm:text-6xl">
        We build
        <span class="relative whitespace-nowrap text-brand-blue dark:text-brand-yellow">
          digital products
          <span
            class="absolute inset-x-0 -bottom-1 h-1 rounded-full bg-brand-yellow dark:bg-brand-blue"
          ></span>
        </span>
        that grow your business
      </h1>

      <p class="max-w-xl text-lg text-slate-600 dark:text-slate-300">
        JD Nexus Digital designs and builds websites, web apps, and custom
        software tailored to your business needs.
      </p>

      <div class="mt-4 flex flex-wrap items-center justify-center gap-4">
        <a
          href="#contact"
          class="rounded-lg border-2 border-brand-blue bg-transparent px-6 py-3 font-medium text-brand-blue transition hover:bg-brand-blue/10 active:bg-brand-blue/10 dark:border-brand-yellow dark:text-brand-yellow dark:hover:bg-brand-yellow/10 dark:active:bg-brand-yellow/10"
        >
          Get in touch
        </a>
        <a
          href="#services"
          class="rounded-lg border-2 border-brand-blue bg-transparent px-6 py-3 font-medium text-brand-blue transition hover:bg-brand-blue/10 active:bg-brand-blue/10 dark:border-brand-yellow dark:text-brand-yellow dark:hover:bg-brand-yellow/10 dark:active:bg-brand-yellow/10"
        >
          Our services
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.badge-cursor {
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
  .badge-cursor {
    animation: none;
  }
}
</style>
