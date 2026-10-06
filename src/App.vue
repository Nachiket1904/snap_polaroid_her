<script setup lang="ts">
import { RouterView } from 'vue-router'
import { inject } from '@vercel/analytics'
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'

// Initialize Vercel Analytics
inject()
</script>

<template>
  <div class="min-h-screen flex flex-col bg-slate-50">
    <Navbar />
    <main class="flex-1">
      <RouterView />
    </main>
    <Footer />
  </div>
</template>
