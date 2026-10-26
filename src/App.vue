<script setup>
import SiteHeader from './components/SiteHeader.vue'
import HeroSection from './components/HeroSection.vue'
import VideoIntro from './components/VideoIntro.vue'
import AudienceSection from './components/AudienceSection.vue'
import StepsSlider from './components/StepsSlider.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import FaqSection from './components/FaqSection.vue'
import ContactForm from './components/ContactForm.vue'
import SocialsSection from './components/SocialsSection.vue'
import SiteFooter from './components/SiteFooter.vue'
</script>

<template>
  <!-- soft background light for the glass to refract -->
  <div
    class="pointer-events-none fixed inset-0 -z-10 overflow-hidden"
    aria-hidden="true"
  >
    <div
      class="absolute -left-32 -top-24 h-[28rem] w-[28rem] rounded-full bg-sky-300/50 blur-3xl"
    ></div>
    <div
      class="absolute right-[-8rem] top-1/3 h-[30rem] w-[30rem] rounded-full bg-indigo-300/40 blur-3xl"
    ></div>
    <div
      class="absolute bottom-[-8rem] left-1/4 h-[26rem] w-[26rem] rounded-full bg-cyan-200/50 blur-3xl"
    ></div>
  </div>

  <SiteHeader />
  <main>
    <HeroSection />
    <VideoIntro />
    <AudienceSection />
    <StepsSlider />
    <ProjectsSection />
    <FaqSection />
    <ContactForm />
    <SocialsSection />
  </main>
  <SiteFooter />
</template>
