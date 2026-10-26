<script setup>
import { projects } from '../data'
</script>

<template>
  <section id="projects" class="section">
    <h2 class="h2 text-center">My projects</h2>
    <div class="mt-12 grid gap-5 md:grid-cols-2 lg:grid-cols-3">
      <a v-for="p in projects" :key="p.title" :href="p.href"
         class="glass group block rounded-3xl p-7 transition hover:-translate-y-1">
        <div class="aspect-video rounded-2xl bg-gradient-to-br from-sky-200 via-indigo-100 to-cyan-100"></div>
        <p class="mt-5 text-sm text-muted">{{ p.niche }}</p>
        <h3 class="mt-1 text-xl font-bold">{{ p.title }}</h3>
        <p class="mt-2 text-muted">{{ p.text }}</p>
        <dl class="mt-6 grid grid-cols-3 gap-2 border-t border-white/70 pt-5">
          <div v-for="s in p.stats" :key="s.l">
            <dt class="sr-only">{{ s.l }}</dt>
            <dd class="text-2xl font-bold">{{ s.v }}</dd>
            <dd class="text-xs text-muted">{{ s.l }}</dd>
          </div>
        </dl>
      </a>
    </div>
  </section>
</template>
