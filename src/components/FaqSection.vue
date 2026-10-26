<script setup>
import { ref } from 'vue'
import { faq } from '../data'
const open = ref(0)
</script>

<template>
  <section id="faq" class="section">
    <h2 class="h2 text-center">FAQ</h2>
    <div class="mx-auto mt-12 grid max-w-3xl gap-3">
      <div v-for="(f, n) in faq" :key="f.q" class="glass rounded-3xl">
        <button class="flex w-full items-center justify-between gap-4 px-6 py-5 text-left font-semibold"
                :aria-expanded="open === n" @click="open = open === n ? -1 : n">
          {{ f.q }}
          <svg class="shrink-0 transition-transform duration-300" :class="open === n && 'rotate-45'"
               width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round">
            <path d="M12 5v14M5 12h14" />
          </svg>
        </button>
        <!-- grid-rows trick gives a smooth height animation -->
        <div class="grid transition-[grid-template-rows] duration-300" :style="{ gridTemplateRows: open === n ? '1fr' : '0fr' }">
          <p class="overflow-hidden px-6 text-muted" :class="open === n && 'pb-5'">{{ f.a }}</p>
        </div>
      </div>
    </div>
  </section>
</template>
