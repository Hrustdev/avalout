<script setup>
import { socials } from '../data'
</script>

<template>
  <section class="section !py-10">
    <div class="flex flex-wrap items-center justify-center gap-3">
      <span class="w-full text-center text-sm text-muted sm:w-auto sm:pr-3">Find me on</span>
      <a v-for="s in socials" :key="s.label" :href="s.href" target="_blank" rel="noopener" class="btn-glass">{{ s.label }}</a>
    </div>
  </section>
</template>
