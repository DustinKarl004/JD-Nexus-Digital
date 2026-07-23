<script setup>
import { useTheme } from '../composables/useTheme'

const { theme, toggleTheme } = useTheme()
</script>

<template>
  <button
    type="button"
    class="flex size-10 items-center justify-center rounded-full border border-slate-300 transition hover:border-brand-blue active:border-brand-blue dark:border-slate-600 dark:hover:border-brand-yellow dark:active:border-brand-yellow"
    :aria-label="theme === 'dark' ? 'Switch to light mode' : 'Switch to dark mode'"
    @click="toggleTheme"
  >
    <svg
      v-if="theme === 'dark'"
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 24 24"
      fill="none"
      stroke-width="1.75"
      stroke-linecap="round"
      stroke-linejoin="round"
      class="size-5 text-brand-yellow"
    >
      <circle cx="12" cy="12" r="4" stroke="currentColor" />
      <path
        stroke="currentColor"
        d="M12 2v2M12 20v2M4.93 4.93l1.41 1.41M17.66 17.66l1.41 1.41M2 12h2M20 12h2M4.93 19.07l1.41-1.41M17.66 6.34l1.41-1.41"
      />
    </svg>
    <svg
      v-else
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 24 24"
      fill="none"
      stroke-width="1.75"
      stroke-linecap="round"
      stroke-linejoin="round"
      class="size-5 text-brand-blue"
    >
      <path
        stroke="currentColor"
        d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79Z"
      />
    </svg>
  </button>
</template>
