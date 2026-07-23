<script setup>
const values = [
  {
    title: 'Quality',
    description: 'We build things properly the first time, not just fast.',
  },
  {
    title: 'Communication',
    description: "You'll always know what's happening with your project.",
  },
  {
    title: 'Reliability',
    description: 'Once we commit to a timeline, we deliver on it.',
  },
]
</script>

<template>
  <section id="about" class="scroll-mt-20 border-t border-slate-200 px-4 py-20 sm:px-6 dark:border-slate-700">
    <div class="mx-auto max-w-5xl">
      <div class="mx-auto mb-12 max-w-2xl text-center">
        <h2 class="text-3xl font-bold sm:text-4xl">About Us</h2>
        <p class="mt-3 text-slate-600 dark:text-slate-300">
          We're a web and software development studio focused on building
          digital products that actually help businesses grow.
        </p>
      </div>

      <div class="grid grid-cols-1 gap-6 md:grid-cols-3">
        <div
          v-for="value in values"
          :key="value.title"
          class="rounded-xl border border-slate-200 p-6 dark:border-slate-700"
        >
          <div class="mb-3 h-1 w-10 rounded-full bg-brand-yellow"></div>
          <h3 class="mb-2 text-lg font-semibold">{{ value.title }}</h3>
          <p class="text-sm text-slate-600 dark:text-slate-300">
            {{ value.description }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>
