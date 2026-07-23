<script setup>
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
    </div>
  </section>
</template>
