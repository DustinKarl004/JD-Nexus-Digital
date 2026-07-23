<script setup>
import { reactive, ref, useTemplateRef } from 'vue'
import emailjs from '@emailjs/browser'

const SERVICE_ID = import.meta.env.VITE_EMAILJS_SERVICE_ID
const TEMPLATE_ID = import.meta.env.VITE_EMAILJS_TEMPLATE_ID
const PUBLIC_KEY = import.meta.env.VITE_EMAILJS_PUBLIC_KEY

const formRef = useTemplateRef('contact-form')

const form = reactive({
  name: '',
  email: '',
  message: '',
})

const status = ref('idle') // idle | sending | success | error

async function handleSubmit() {
  if (!SERVICE_ID || !TEMPLATE_ID || !PUBLIC_KEY) {
    status.value = 'error'
    return
  }

  status.value = 'sending'

  try {
    await emailjs.sendForm(SERVICE_ID, TEMPLATE_ID, formRef.value, {
      publicKey: PUBLIC_KEY,
    })

    status.value = 'success'
    form.name = ''
    form.email = ''
    form.message = ''
  } catch {
    status.value = 'error'
  }
}
</script>

<template>
  <section id="contact" class="scroll-mt-20 border-t border-slate-200 px-4 py-20 sm:px-6 dark:border-slate-700">
    <div class="mx-auto max-w-2xl text-center">
      <h2 class="text-3xl font-bold sm:text-4xl">Let's build something together</h2>
      <p class="mt-3 text-slate-600 dark:text-slate-300">
        Have a project in mind? Send us a message and we'll get back to you.
      </p>
    </div>

    <form
      ref="contact-form"
      class="mx-auto mt-10 flex max-w-xl flex-col gap-4 text-left"
      @submit.prevent="handleSubmit"
    >
      <div>
        <label for="name" class="mb-1 block text-sm font-medium">Name</label>
        <input
          id="name"
          v-model="form.name"
          type="text"
          name="from_name"
          required
          class="w-full rounded-lg border border-slate-300 bg-transparent px-4 py-2 outline-none transition focus:border-brand-blue dark:border-slate-600 dark:focus:border-brand-yellow"
        />
      </div>

      <div>
        <label for="email" class="mb-1 block text-sm font-medium">Email</label>
        <input
          id="email"
          v-model="form.email"
          type="email"
          name="from_email"
          required
          class="w-full rounded-lg border border-slate-300 bg-transparent px-4 py-2 outline-none transition focus:border-brand-blue dark:border-slate-600 dark:focus:border-brand-yellow"
        />
      </div>

      <div>
        <label for="message" class="mb-1 block text-sm font-medium">Message</label>
        <textarea
          id="message"
          v-model="form.message"
          name="message"
          rows="5"
          required
          class="w-full rounded-lg border border-slate-300 bg-transparent px-4 py-2 outline-none transition focus:border-brand-blue dark:border-slate-600 dark:focus:border-brand-yellow"
        ></textarea>
      </div>

      <button
        type="submit"
        :disabled="status === 'sending'"
        class="mt-2 inline-flex items-center justify-center rounded-lg border-2 border-brand-yellow bg-brand-blue px-8 py-3 font-medium text-white transition hover:bg-brand-blue-light disabled:cursor-not-allowed disabled:opacity-60"
      >
        {{ status === 'sending' ? 'Sending...' : 'Send message' }}
      </button>

      <p v-if="status === 'success'" class="text-sm text-emerald-600 dark:text-emerald-400">
        Thanks! Your message has been sent — we'll get back to you soon.
      </p>
      <p v-if="status === 'error'" class="break-words text-sm text-red-600 dark:text-red-400">
        Something went wrong. Please email us directly at
        <a href="mailto:dustinabalos677@gmail.com" class="underline">dustinabalos677@gmail.com</a>.
      </p>
    </form>
  </section>
</template>
