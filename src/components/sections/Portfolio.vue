<script setup>
import healthmemoLogo from '../../assets/portfolio/healthmemo.png'
import zaCompanyLogo from '../../assets/portfolio/za-company.png'
import applypaLogo from '../../assets/portfolio/applypa.png'

const projects = [
  {
    name: 'HealthMemo',
    logo: healthmemoLogo,
    description:
      'HIPAA-compliant medicolegal case management system with OCR document processing, async task queues, cloud storage, and billing — deployed as a full multi-tenant admin dashboard.',
    tags: ['Django', 'Vue.js', 'Celery', 'Redis', 'AWS', 'Stripe', 'Docker'],
    url: 'https://staging.healthmemo.com/auth/signin',
  },
  {
    name: 'Z.A. Company',
    logo: zaCompanyLogo,
    description:
      'Inventory and sales management system for branch operations — tracking stocks, sales, and profit per branch every day, with a clean sign-in and dashboard experience.',
    tags: ['Vue.js', 'Python', 'PostgreSQL', 'Railway', 'Vercel'],
    url: 'https://z-a-company.vercel.app/login',
  },
  {
    name: 'Applypa',
    logo: applypaLogo,
    description:
      'Job board for Filipino remote workers with search & filtering, saved jobs, resume builder, cover letter generator, application tracking, and email notifications.',
    tags: ['Django', 'Vue.js', 'PostgreSQL', 'Celery', 'Brevo'],
    url: 'https://www.applypa.com/',
  },
]
</script>

<template>
  <section id="portfolio" class="scroll-mt-20 border-t border-slate-200 px-4 py-20 sm:px-6 dark:border-slate-700">
    <div class="mx-auto max-w-5xl">
      <div class="mb-12 text-center">
        <h2 class="text-3xl font-bold sm:text-4xl">Our Work</h2>
        <p class="mt-3 text-slate-600 dark:text-slate-300">
          A few products we've built and shipped
        </p>
      </div>

      <div class="grid grid-cols-1 gap-6 md:grid-cols-3">
        <a
          v-for="project in projects"
          :key="project.name"
          :href="project.url"
          target="_blank"
          rel="noopener noreferrer"
          class="group relative flex flex-col overflow-hidden rounded-xl border border-slate-200 p-6 text-left transition hover:border-brand-blue hover:shadow-lg dark:border-slate-700 dark:hover:border-brand-yellow"
        >
          <div
            class="absolute inset-x-0 top-0 h-1 bg-brand-blue opacity-0 transition group-hover:opacity-100"
          />
          <div class="mb-3 flex items-center gap-3">
            <img
              :src="project.logo"
              :alt="project.name"
              class="size-10 shrink-0 rounded-lg object-contain"
            />
            <h3 class="text-lg font-semibold">{{ project.name }}</h3>
          </div>
          <p class="mb-4 flex-1 text-sm text-slate-600 dark:text-slate-300">
            {{ project.description }}
          </p>
          <div class="mb-4 flex flex-wrap gap-2">
            <span
              v-for="tag in project.tags"
              :key="tag"
              class="rounded-full bg-brand-yellow/15 px-2.5 py-1 text-xs font-medium text-slate-700 dark:bg-brand-yellow/30 dark:text-slate-200"
            >
              {{ tag }}
            </span>
          </div>
          <span class="text-sm font-medium text-brand-blue dark:text-brand-yellow">
            View live &rarr;
          </span>
        </a>
      </div>
    </div>
  </section>
</template>
