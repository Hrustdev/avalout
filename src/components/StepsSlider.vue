<script setup>
import { ref, computed, onMounted, onBeforeUnmount } from 'vue'
import { steps } from '../data'

const i = ref(0)
const paused = ref(false)
let timer
const go = (n) => (i.value = (n + steps.length) % steps.length)
const track = computed(() => ({ transform: `translateX(-${i.value * 100}%)` }))

onMounted(() => { timer = setInterval(() => !paused.value && go(i.value + 1), 5000) })
onBeforeUnmount(() => clearInterval(timer))
</script>

<template>
  <section id="process" class="section">
    <h2 class="h2 text-center">How it works</h2>

    <div class="mx-auto mt-12 max-w-3xl" @mouseenter="paused = true" @mouseleave="paused = false">
      <div class="glass overflow-hidden rounded-[2rem]">
        <div class="flex transition-transform duration-700 ease-[cubic-bezier(.22,1,.36,1)]" :style="track">
          <article v-for="(s, n) in steps" :key="s.title" class="w-full shrink-0 p-8 sm:p-12"
                   :aria-hidden="n !== i">
            <span class="grid h-12 w-12 place-items-center rounded-full bg-white/70 text-lg font-bold shadow-inner">{{ n + 1 }}</span>
            <h3 class="mt-6 text-2xl font-bold sm:text-3xl">{{ s.title }}</h3>
            <p class="mt-3 min-h-[5rem] max-w-xl text-lg text-muted">{{ s.text }}</p>
          </article>
        </div>
      </div>

      <div class="mt-6 flex items-center justify-between">
        <div class="flex gap-2">
          <button v-for="(s, n) in steps" :key="n" :aria-label="`Go to step ${n + 1}`" @click="go(n)"
                  class="h-2.5 rounded-full transition-all duration-300"
                  :class="n === i ? 'w-8 bg-accent' : 'w-2.5 bg-ink/20'"></button>
        </div>
        <div class="flex gap-2">
          <button class="btn-glass !h-11 !w-11 !p-0" aria-label="Previous step" @click="go(i - 1)">‹</button>
          <button class="btn-glass !h-11 !w-11 !p-0" aria-label="Next step" @click="go(i + 1)">›</button>
        </div>
      </div>
    </div>
  </section>
</template>
