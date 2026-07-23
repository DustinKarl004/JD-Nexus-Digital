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
          class="rounded-xl border border-slate-200 bg-white p-6 shadow-sm dark:border-slate-700 dark:bg-slate-800/50"
        >
          <div class="mb-3 h-1 w-10 rounded-full bg-brand-yellow"></div>
          <h3 class="mb-2 text-lg font-semibold">{{ value.title }}</h3>
          <p class="text-sm text-slate-600 dark:text-slate-300">
            {{ value.description }}
          </p>
        </div>
      </div>

      <div class="mx-auto mt-12 flex max-w-2xl flex-col items-center gap-3 text-center">
        <p class="text-sm text-slate-600 dark:text-slate-300">
          Follow our journey and see what we're building.
        </p>
        <a
          href="https://www.facebook.com/jdnexusdigital/"
          target="_blank"
          rel="noopener noreferrer"
          class="inline-flex items-center gap-2 rounded-lg border-2 border-brand-blue bg-transparent px-5 py-2.5 font-medium text-brand-blue transition hover:bg-brand-blue/10 active:bg-brand-blue/10 dark:border-brand-yellow dark:text-brand-yellow dark:hover:bg-brand-yellow/10 dark:active:bg-brand-yellow/10"
        >
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="size-5">
            <path
              d="M22 12a10 10 0 1 0-11.56 9.88v-6.99H7.9V12h2.54V9.8c0-2.5 1.49-3.89 3.77-3.89 1.09 0 2.23.2 2.23.2v2.45h-1.26c-1.24 0-1.63.77-1.63 1.56V12h2.78l-.44 2.89h-2.34v6.99A10 10 0 0 0 22 12Z"
            />
          </svg>
          Follow us on Facebook
        </a>
      </div>
    </div>
  </section>
</template>
