<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isMenuOpen = ref(false)
const isScrolled = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
  isMenuOpen.value = false
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <nav
      :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-300',
      isScrolled
        ? 'bg-white/95 backdrop-blur-lg shadow-lg border-b border-gray-200/50'
        : 'bg-transparent'
    ]"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <!-- Logo -->
        <div class="flex-shrink-0">
          <button
              @click="scrollToSection('hero')"
              class="flex items-center space-x-2 group"
          >
            <div
                :class="[
                'w-10 h-10 rounded-lg flex items-center justify-center font-bold text-lg transition-all duration-300 transform group-hover:scale-110',
                isScrolled
                  ? 'bg-blue-600 text-white'
                  : 'bg-white/20 backdrop-blur-sm text-white border border-white/30'
              ]"
            >
              MH
            </div>
            <span
                :class="[
                'font-bold text-lg transition-colors duration-300',
                isScrolled ? 'text-gray-900' : 'text-white'
              ]"
            >
              Maxime Heim
            </span>
          </button>
        </div>

        <!-- Desktop Menu -->
        <div class="hidden md:block">
          <div class="ml-10 flex items-center space-x-1">
            <a
                v-for="item in menuItems"
                :key="item.id"
                @click="scrollToSection(item.id)"
                :class="[
                'px-4 py-2 rounded-lg text-sm font-medium cursor-pointer transition-all duration-200 hover:scale-105',
                isScrolled
                  ? 'text-gray-600 hover:text-blue-600 hover:bg-blue-50'
                  : 'text-white/80 hover:text-white hover:bg-white/10 backdrop-blur-sm'
              ]"
            >
              {{ item.name }}
            </a>


          </div>
        </div>

        <!-- Mobile menu button -->
        <div class="md:hidden">
          <button
              @click="toggleMenu"
              :class="[
              'p-2 rounded-lg transition-all duration-200',
              isScrolled
                ? 'text-gray-600 hover:text-blue-600 hover:bg-blue-50'
                : 'text-white hover:text-white hover:bg-white/10'
            ]"
          >
            <svg
                class="w-6 h-6 transition-transform duration-200"
                :class="{ 'rotate-90': isMenuOpen }"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
            >
              <path
                  v-if="!isMenuOpen"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M4 6h16M4 12h16M4 18h16"
              />
              <path
                  v-else
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M6 18L18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
      </div>

      <!-- Mobile Menu -->
      <div
          :class="[
          'md:hidden transition-all duration-300 overflow-hidden',
          isMenuOpen ? 'max-h-96 opacity-100' : 'max-h-0 opacity-0'
        ]"
      >
        <div
            :class="[
            'py-4 space-y-2 border-t',
            isScrolled ? 'border-gray-200' : 'border-white/20'
          ]"
        >
          <a
              v-for="item in menuItems"
              :key="item.id"
              @click="scrollToSection(item.id)"
              :class="[
              'block px-4 py-3 rounded-lg text-base font-medium cursor-pointer transition-all duration-200',
              isScrolled
                ? 'text-gray-600 hover:text-blue-600 hover:bg-blue-50'
                : 'text-white/80 hover:text-white hover:bg-white/10'
            ]"
          >
            {{ item.name }}
          </a>

          <button
              @click="scrollToSection('contact')"
              :class="[
              'w-full text-left px-4 py-3 rounded-lg text-base font-bold transition-all duration-200',
              isScrolled
                ? 'bg-blue-600 text-white hover:bg-blue-700'
                : 'bg-white text-blue-900 hover:bg-blue-50'
            ]"
          >
            Contact
          </button>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      menuItems: [
        { id: 'experience', name: 'Expériences' },
        { id: 'projects', name: 'Projets' }
      ]
    }
  }
}
</script>