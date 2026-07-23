<script setup>
import zaCompanyLogo from '../../assets/portfolio/za-company.png'
import fullStackTutorialLogo from '../../assets/portfolio/fullstacktutorial.svg'
import jdNexusLogo from '../../assets/JD_Logo.webp'

const projects = [
  {
    name: 'JD Nexus Digital',
    logo: jdNexusLogo,
    description:
      'Our own agency website — a fast, responsive landing page with a portfolio showcase and contact form powered by EmailJS.',
    tags: ['Vue.js', 'Tailwind CSS', 'Vite', 'EmailJS'],
    url: 'https://jd-nexus-digital.vercel.app/',
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
    name: 'FullStackTutorial',
    logo: fullStackTutorialLogo,
    description:
      'Educational platform offering structured, step-by-step tutorials for learning full-stack web development, from frontend fundamentals to backend systems and deployment.',
    tags: ['TypeScript', 'SCSS', 'JavaScript'],
    url: 'https://full-stack-tutorial-gamma.vercel.app/',
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
          class="group relative flex flex-col overflow-hidden rounded-xl border border-slate-200 bg-white p-6 text-left shadow-sm transition hover:border-brand-blue hover:shadow-lg dark:border-slate-700 dark:bg-slate-800/50 dark:hover:border-brand-yellow"
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
              class="rounded-full bg-brand-blue/10 px-2.5 py-1 text-xs font-medium text-slate-700 dark:bg-brand-blue/20 dark:text-slate-200"
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
