<script setup>
import { ref } from 'vue'
// Replace with your friend's real video (YouTube embed URL)
const VIDEO_URL = 'https://www.youtube.com/embed/dQw4w9WgXcQ?autoplay=1'
const playing = ref(false)
</script>

<template>
  <section id="intro" class="section">
    <div class="mx-auto max-w-4xl text-center">
      <h2 class="h2">Hi, I’m Dan</h2>
      <p class="mx-auto mt-3 max-w-lg text-muted">
        Watch a short intro on how I build YouTube channels for founders.
      </p>
    </div>

    <div
      class="glass mx-auto mt-10 max-w-4xl overflow-hidden rounded-[2rem] p-2 sm:p-3"
    >
      <div
        class="relative aspect-video overflow-hidden rounded-[1.5rem] bg-gradient-to-br from-sky-200 to-indigo-200"
      >
        <iframe
          v-if="playing"
          :src="VIDEO_URL"
          title="Intro video"
          class="absolute inset-0 h-full w-full"
          allow="autoplay; encrypted-media; picture-in-picture"
          allowfullscreen
        ></iframe>
        <button
          v-else
          class="group absolute inset-0 grid place-items-center"
          aria-label="Play intro video"
          @click="playing = true"
        >
          <span
            class="glass grid h-20 w-20 place-items-center rounded-full transition group-hover:scale-110"
          >
            <svg width="28" height="28" viewBox="0 0 24 24" fill="#16233b">
              <path d="M8 5v14l11-7z" />
            </svg>
          </span>
        </button>
      </div>
    </div>
  </section>
</template>
