<script setup>
import { ref } from 'vue'

const faqs = [
  {
    question: 'How much does a project cost?',
    answer:
      'It depends on scope and complexity. Reach out with details about your project and we\'ll give you a clear quote.',
  },
  {
    question: 'How long does a typical project take?',
    answer:
      'A simple website usually takes a few weeks. Custom software or larger web apps can take longer — we\'ll give you a realistic timeline after discussing your requirements.',
  },
  {
    question: 'Do you offer support after launch?',
    answer:
      'Yes. We offer ongoing maintenance and support to keep your product running smoothly after it goes live.',
  },
  {
    question: 'Can you work with an existing codebase?',
    answer:
      'Yes, we can review, maintain, or extend an existing project as needed.',
  },
]

const openIndex = ref(null)

function toggle(index) {
  openIndex.value = openIndex.value === index ? null : index
}
</script>

<template>
  <section id="faq" class="scroll-mt-20 border-t border-slate-200 px-4 py-20 sm:px-6 dark:border-slate-700">
    <div class="mx-auto max-w-2xl">
      <div class="mb-12 text-center">
        <h2 class="text-3xl font-bold sm:text-4xl">Frequently Asked Questions</h2>
      </div>

      <div class="flex flex-col gap-3">
        <div
          v-for="(faq, index) in faqs"
          :key="faq.question"
          class="rounded-xl border border-slate-200 dark:border-slate-700"
        >
          <button
            type="button"
            class="flex w-full items-center justify-between gap-4 px-5 py-4 text-left font-medium"
            :aria-expanded="openIndex === index"
            @click="toggle(index)"
          >
            <span class="min-w-0 flex-1">{{ faq.question }}</span>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="1.75"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="size-5 shrink-0 text-brand-blue transition-transform dark:text-brand-yellow"
              :class="{ 'rotate-180': openIndex === index }"
            >
              <path d="M6 9l6 6 6-6" />
            </svg>
          </button>
          <Transition
            enter-active-class="transition-all duration-200 ease-out"
            enter-from-class="grid-rows-[0fr] opacity-0"
            enter-to-class="grid-rows-[1fr] opacity-100"
            leave-active-class="transition-all duration-150 ease-in"
            leave-from-class="grid-rows-[1fr] opacity-100"
            leave-to-class="grid-rows-[0fr] opacity-0"
          >
            <div v-if="openIndex === index" class="grid">
              <p class="overflow-hidden px-5 pb-4 text-sm text-slate-600 dark:text-slate-300">
                {{ faq.answer }}
              </p>
            </div>
          </Transition>
        </div>
      </div>
    </div>
  </section>
</template>
