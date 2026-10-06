<script setup lang="ts">
const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="mt-auto py-6 text-center">
    <div class="glass-card max-w-6xl mx-auto px-4 py-4">
      <p class="text-gray-600 text-sm">
        Made by <span class="font-medium text-purple-600">Nachiket Kapure</span>
      </p>
      <p class="text-gray-400 text-xs mt-2">© {{ currentYear }} SnapNest. Made with 💜</p>
    </div>
  </footer>
</template>
