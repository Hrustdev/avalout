<script setup>
import { audience } from '../data'
</script>

<template>
  <section id="audience" class="section">
    <h2 class="h2 text-center">Who it’s for</h2>
    <div class="mt-12 grid gap-5 md:grid-cols-3">
      <article v-for="a in audience" :key="a.title" class="glass rounded-3xl p-7">
        <h3 class="text-xl font-bold">{{ a.title }}</h3>
        <p class="mt-3 text-muted">{{ a.text }}</p>
      </article>
    </div>
  </section>
</template>
