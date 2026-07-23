<script setup>
import { ref } from 'vue'
import ThemeToggle from './components/ThemeToggle.vue'
import Hero from './components/sections/Hero.vue'
import About from './components/sections/About.vue'
import Services from './components/sections/Services.vue'
import Portfolio from './components/sections/Portfolio.vue'
import Process from './components/sections/Process.vue'
import FAQ from './components/sections/FAQ.vue'
import Contact from './components/sections/Contact.vue'
import logo from './assets/logo.png'

const navLinks = [
  { to: '#about', label: 'About' },
  { to: '#services', label: 'Services' },
  { to: '#portfolio', label: 'Work' },
  { to: '#process', label: 'Process' },
  { to: '#faq', label: 'FAQ' },
  { to: '#contact', label: 'Contact' },
]

const mobileMenuOpen = ref(false)
</script>

<template>
  <div class="flex min-h-svh flex-col">
    <header
      class="sticky top-0 z-10 border-b border-slate-200 bg-white/80 backdrop-blur dark:border-slate-700 dark:bg-slate-900/80"
    >
      <div class="flex items-center justify-between px-4 py-3 sm:px-6 sm:py-4">
        <a
          href="#"
          class="flex items-center gap-1.5 text-base font-semibold text-brand-blue sm:gap-2 sm:text-lg dark:text-white"
          @click="mobileMenuOpen = false"
        >
          <span class="flex size-8 shrink-0 items-center justify-center rounded-lg p-1 dark:bg-white">
            <img :src="logo" alt="JD Nexus Digital" class="size-full object-contain" />
          </span>
          <span class="truncate">JD Nexus Digital</span>
        </a>

        <nav class="hidden items-center gap-6 md:flex">
          <a
            v-for="link in navLinks"
            :key="link.to"
            :href="link.to"
            class="text-sm font-medium text-slate-600 transition hover:text-brand-blue dark:text-slate-300 dark:hover:text-brand-yellow"
          >
            {{ link.label }}
          </a>
        </nav>

        <div class="flex items-center gap-2">
          <ThemeToggle />
          <button
            type="button"
            class="flex size-10 items-center justify-center rounded-full border border-slate-300 dark:border-slate-600 md:hidden"
            :aria-expanded="mobileMenuOpen"
            aria-label="Toggle menu"
            @click="mobileMenuOpen = !mobileMenuOpen"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="1.75"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="size-5"
            >
              <path v-if="!mobileMenuOpen" d="M4 6h16M4 12h16M4 18h16" />
              <path v-else d="M6 6l12 12M18 6l-12 12" />
            </svg>
          </button>
        </div>
      </div>

      <nav
        v-if="mobileMenuOpen"
        class="flex flex-col gap-1 border-t border-slate-200 px-4 py-4 sm:px-6 md:hidden dark:border-slate-700"
      >
        <a
          v-for="link in navLinks"
          :key="link.to"
          :href="link.to"
          class="rounded-md px-3 py-2 text-sm font-medium text-slate-600 transition hover:bg-brand-blue/5 hover:text-brand-blue dark:text-slate-300 dark:hover:text-brand-yellow"
          @click="mobileMenuOpen = false"
        >
          {{ link.label }}
        </a>
      </nav>
    </header>

    <main class="flex-1">
      <Hero />
      <About />
      <Services />
      <Portfolio />
      <Process />
      <FAQ />
      <Contact />
    </main>

    <footer class="border-t border-slate-200 px-4 py-4 text-center text-sm text-slate-500 sm:px-6 dark:border-slate-700 dark:text-slate-400">
      &copy; {{ new Date().getFullYear() }} JD Nexus Digital. All rights reserved.
    </footer>
  </div>
</template>
