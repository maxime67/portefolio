<template>
  <footer class="bg-gray-900 text-white">
    <div class="border-t border-gray-800">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6">
        <div class="flex flex-col md:flex-row justify-between items-center space-y-4 md:space-y-0">
          <!-- Copyright -->
          <div class="flex items-center space-x-4 text-gray-400">
            <span>© {{ currentYear }} Maxime Heim. Tous droits réservés.</span>
          </div>
          <div v-for="link in socialLinks" :key="link.id"
               class=" flex flex-col md:flex-row justify-between items-center space-y-4 md:space-y-0">
            <a target="_blank" :href="link.url">
            <div class="rounded-2xl bg-gradient-to-br p-1 text-white" :class="link.color">
              <span class="inline-block px-3 py-1   text-sm font-medium">
                  {{ link.name }}
                </span>
            </div>
            </a>
          </div>
          <!-- Tech Stack Badge -->
          <div class="flex items-center space-x-2 text-gray-400 text-sm">
            <span>Fait avec</span>
            <div class="flex items-center space-x-1">
              <span class="text-green-400">💚</span>
              <span>Vue.js</span>
            </div>
            <span>&</span>
            <div class="flex items-center space-x-1">
              <span class="text-blue-400">🎨</span>
              <span>Tailwind CSS</span>
            </div>
          </div>
        </div>


        <!-- Back to Top Button -->
        <button
            v-show="showBackToTop"
            @click="scrollToTop"
            class="fixed bottom-8 right-8 w-12 h-12 bg-gradient-to-r from-blue-600 to-purple-600 text-white rounded-full shadow-lg hover:shadow-xl transition-all duration-300 transform hover:scale-110 z-40 flex items-center justify-center"
            title="Retour en haut"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18"></path>
          </svg>
        </button>
      </div>
    </div>
  </footer>
</template>

<script setup>
import {ref, computed, onMounted, onUnmounted} from 'vue'

const showBackToTop = ref(false)

const currentYear = computed(() => new Date().getFullYear())

const socialLinks = ref([
  {
    name: 'GitHub',
    url: 'https://github.com/maxime67',
    color: 'from-blue-400 to-purple-700'
  },
  {
    name: 'LinkedIn',
    url: 'https://www.linkedin.com/in/maxime-heim-482324264',
    color: 'from-blue-500 to-purple-700'
  },
  {
    name: 'Email',
    url: 'mailto:maxime.heim3@gmail.com',
    color: 'from-blue-600 to-purple-800'
  }
])

const scrollToTop = () => {
  window.scrollTo({top: 0, behavior: 'smooth'})
}

const handleScroll = () => {
  showBackToTop.value = window.scrollY > 300
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>