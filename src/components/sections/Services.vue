<script setup>
const services = [
  {
    title: 'Web Development',
    description:
      'Fast, responsive websites built with modern frameworks and best practices.',
    icon: '🌐',
  },
  {
    title: 'Custom Software',
    description:
      'Tailored applications designed around your specific workflows and goals.',
    icon: '⚙️',
  },
  {
    title: 'Web Apps',
    description:
      'Interactive, scalable web applications with clean, maintainable code.',
    icon: '💻',
  },
  {
    title: 'Maintenance & Support',
    description:
      'Ongoing updates, fixes, and improvements to keep your product running smoothly.',
    icon: '🛠️',
  },
]
</script>

<template>
  <section id="services" class="scroll-mt-20 border-t border-slate-200 px-4 py-20 sm:px-6 dark:border-slate-700">
    <div class="mx-auto max-w-5xl">
      <div class="mb-12 text-center">
        <h2 class="text-3xl font-bold sm:text-4xl">Our Services</h2>
        <p class="mt-3 text-slate-600 dark:text-slate-300">
          What we can build for you
        </p>
      </div>

      <div class="grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-4">
        <div
          v-for="service in services"
          :key="service.title"
          class="group relative overflow-hidden rounded-xl border border-slate-200 bg-white p-6 text-left shadow-sm transition hover:border-brand-blue hover:shadow-lg active:border-brand-blue active:shadow-lg dark:border-slate-700 dark:bg-slate-800/50 dark:hover:border-brand-yellow dark:active:border-brand-yellow"
        >
          <div
            class="absolute inset-x-0 top-0 h-1 bg-brand-blue opacity-0 transition group-hover:opacity-100 group-active:opacity-100"
          />
          <div
            class="mb-4 flex size-11 items-center justify-center rounded-lg bg-brand-blue/10 text-2xl dark:bg-brand-blue/20"
          >
            {{ service.icon }}
          </div>
          <h3 class="mb-2 text-lg font-semibold">{{ service.title }}</h3>
          <p class="text-sm text-slate-600 dark:text-slate-300">
            {{ service.description }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>
