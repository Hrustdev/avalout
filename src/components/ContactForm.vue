<script setup>
import { reactive, ref } from 'vue'

const form = reactive({ name: '', email: '', message: '' })
const status = ref('idle') // idle | sending | sent | error

async function submit() {
  status.value = 'sending'
  try {
    // TODO: connect your backend or a form service (Formspree, Web3Forms, etc.)
    // await fetch('https://your-endpoint', { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(form) })
    await new Promise((r) => setTimeout(r, 800))
    status.value = 'sent'
    Object.assign(form, { name: '', email: '', message: '' })
  } catch {
    status.value = 'error'
  }
}

const field = 'w-full rounded-2xl border border-white/80 bg-white/60 px-4 py-3 outline-none transition placeholder:text-muted/70 focus:border-accent focus:bg-white/90'
</script>

<template>
  <section id="contact" class="section">
    <div class="glass mx-auto max-w-2xl rounded-[2rem] p-7 sm:p-10">
      <h2 class="h2 text-center">Book a strategy call</h2>
      <p class="mt-3 text-center text-muted">Tell me about your business and I’ll reply within one business day.</p>

      <form class="mt-8 grid gap-4" @submit.prevent="submit">
        <label class="grid gap-1.5 text-sm font-medium">Name
          <input v-model.trim="form.name" :class="field" type="text" required autocomplete="name" placeholder="Your name" />
        </label>
        <label class="grid gap-1.5 text-sm font-medium">Email
          <input v-model.trim="form.email" :class="field" type="email" required autocomplete="email" placeholder="you@company.com" />
        </label>
        <label class="grid gap-1.5 text-sm font-medium">Message
          <textarea v-model.trim="form.message" :class="field" rows="4" required placeholder="What do you sell and who to?"></textarea>
        </label>
        <button class="btn-primary mt-2 disabled:opacity-60" :disabled="status === 'sending'">
          {{ status === 'sending' ? 'Sending…' : 'Send message' }}
        </button>
        <p v-if="status === 'sent'" class="text-center text-sm text-emerald-600" role="status">Message sent. I’ll be in touch soon.</p>
        <p v-if="status === 'error'" class="text-center text-sm text-red-600" role="alert">Couldn’t send the message. Please try again.</p>
      </form>
    </div>
  </section>
</template>
