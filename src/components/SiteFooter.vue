<script setup>
import { nav } from '../data'
</script>

<template>
  <footer class="mx-auto max-w-6xl px-5 pb-8 pt-6">
    <div class="glass flex flex-col items-center justify-between gap-5 rounded-3xl px-6 py-6 md:flex-row">
      <a href="#top" class="text-lg font-extrabold">Avalout</a>
      <nav class="flex flex-wrap justify-center gap-x-5 gap-y-2 text-sm text-muted" aria-label="Footer">
        <a v-for="l in nav" :key="l.href" :href="l.href" class="hover:text-ink">{{ l.label }}</a>
      </nav>
      <p class="text-sm text-muted">© {{ new Date().getFullYear() }} Avalout. All rights reserved.</p>
    </div>
  </footer>
</template>
