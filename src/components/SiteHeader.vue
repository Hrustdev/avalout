<script setup>
import { ref } from 'vue'
import { nav } from '../data'
const open = ref(false)
</script>

<template>
  <header class="fixed inset-x-0 top-3 z-50 px-3">
    <div class="glass mx-auto max-w-6xl rounded-full px-5 py-2.5">
      <div class="flex items-center justify-between">
        <a href="#top" class="text-lg font-extrabold tracking-tight">Avalout</a>

        <nav class="hidden items-center gap-1 lg:flex" aria-label="Main">
          <a v-for="l in nav" :key="l.href" :href="l.href"
             class="rounded-full px-3 py-1.5 text-sm font-medium text-muted transition hover:bg-white/60 hover:text-ink">{{ l.label }}</a>
        </nav>

        <div class="flex items-center gap-2">
          <a href="#contact" class="btn-primary hidden !py-2 sm:inline-flex">Book a call</a>
          <button class="grid h-10 w-10 place-items-center rounded-full hover:bg-white/60 lg:hidden"
                  :aria-expanded="open" aria-label="Toggle menu" @click="open = !open">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round">
              <path v-if="!open" d="M4 7h16M4 12h16M4 17h16" /><path v-else d="M6 6l12 12M18 6L6 18" />
            </svg>
          </button>
        </div>
      </div>

      <nav v-show="open" class="mt-3 grid gap-1 border-t border-white/60 pt-3 lg:hidden" aria-label="Mobile">
        <a v-for="l in nav" :key="l.href" :href="l.href" @click="open = false"
           class="rounded-2xl px-3 py-2.5 font-medium hover:bg-white/60">{{ l.label }}</a>
        <a href="#contact" @click="open = false" class="btn-primary mt-1">Book a call</a>
      </nav>
    </div>
  </header>
</template>
