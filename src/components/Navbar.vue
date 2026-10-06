<script setup lang="ts">
import { RouterLink, useRoute } from 'vue-router'
import { ref } from 'vue'
import { Menu, X } from 'lucide-vue-next'

const route = useRoute()
const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}
</script>

<template>
  <nav class="sticky top-0 z-50 glass-card border-b border-gray-200/50">
    <div class="max-w-6xl mx-auto px-4 py-3">
      <div class="flex items-center justify-between">
        <!-- Logo -->
        <RouterLink to="/" class="flex items-center gap-2 group" @click="closeMobileMenu">
          <img 
            src="/favicon.png" 
            alt="Logo" 
            class="w-16 h-16 object-contain transition-all group-hover:scale-110"
          />
          <span class="text-xl font-bold gradient-text">SnapNest</span>
        </RouterLink>

        <!-- Desktop Navigation -->
        <div class="hidden md:flex items-center gap-1">
          <RouterLink
            v-for="link in [
              { to: '/', label: 'Home' },
              { to: '/about', label: 'About' },
              { to: '/privacy', label: 'Privacy' },
              { to: '/layout', label: 'Layout' },
            ]"
            :key="link.to"
            :to="link.to"
            class="px-4 py-2 rounded-full text-sm font-medium transition-all duration-300"
            :class="[
              route.path === link.to
                ? 'bg-purple-100 text-purple-700'
                : 'text-gray-600 hover:text-gray-900 hover:bg-gray-100'
            ]"
          >
            {{ link.label }}
          </RouterLink>
        </div>

        <!-- Right Side Icons -->
        <div class="flex items-center gap-2">
          <!-- Mobile Menu Button -->
          <button 
            @click="toggleMobileMenu"
            class="md:hidden w-10 h-10 rounded-full flex items-center justify-center text-gray-500 hover:bg-gray-100"
          >
            <Menu v-if="!isMobileMenuOpen" class="w-6 h-6" />
            <X v-else class="w-6 h-6" />
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Menu -->
    <div 
      v-show="isMobileMenuOpen"
      class="md:hidden border-t border-gray-100 bg-white/95 backdrop-blur-md absolute w-full left-0 shadow-lg"
    >
      <div class="px-4 py-4 space-y-2">
        <RouterLink
          v-for="link in [
            { to: '/', label: 'Home' },
            { to: '/about', label: 'About' },
            { to: '/privacy', label: 'Privacy' },
            { to: '/layout', label: 'Layout' },
          ]"
          :key="link.to"
          :to="link.to"
          @click="closeMobileMenu"
          class="block px-4 py-3 rounded-xl text-base font-medium transition-colors"
          :class="[
            route.path === link.to
              ? 'bg-purple-50 text-purple-600'
              : 'text-gray-600 hover:bg-gray-50 hover:text-gray-900'
          ]"
        >
          {{ link.label }}
        </RouterLink>
      </div>
    </div>
  </nav>
</template>
