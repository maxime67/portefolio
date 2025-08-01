<template>
  <footer class="bg-gray-900 text-white">
      <div class="border-t border-gray-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6">
          <div class="flex flex-col md:flex-row justify-between items-center space-y-4 md:space-y-0">
            <!-- Copyright -->
            <div class="flex items-center space-x-4 text-gray-400">
              <span>© {{ currentYear }} Maxime Heim. Tous droits réservés.</span>
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

const newsletterEmail = ref('')
const isSubscribing = ref(false)
const showBackToTop = ref(false)
const showModal = ref(false)
const modalContent = ref({})

const currentYear = computed(() => new Date().getFullYear())

const socialLinks = ref([
  {
    name: 'GitHub',
    url: 'https://github.com/maxime67',
    icon: '💻',
    color: 'bg-gray-700 hover:bg-gray-600'
  },
  {
    name: 'LinkedIn',
    url: 'https://linkedin.com/in/maxime-heim',
    icon: '💼',
    color: 'bg-blue-600 hover:bg-blue-500'
  },
  {
    name: 'Twitter',
    url: 'https://twitter.com/maxime_heim',
    icon: '🐦',
    color: 'bg-blue-400 hover:bg-blue-300'
  },
  {
    name: 'Email',
    url: 'mailto:maxime.heim@example.com',
    icon: '📧',
    color: 'bg-red-600 hover:bg-red-500'
  }
])

const quickLinks = ref([
  {name: 'À propos', id: 'about'},
  {name: 'Compétences', id: 'skills'},
  {name: 'Expériences', id: 'experience'},
  {name: 'Projets', id: 'projects'},
  {name: 'Contact', id: 'contact'}
])

const services = ref([
  'Conseil DevOps',
  'Infrastructure Cloud',
  'Développement Full-Stack',
  'Automatisation CI/CD',
  'Formation & Coaching'
])

const legalLinks = ref([
  {name: 'Mentions légales', type: 'legal'},
  {name: 'Politique de confidentialité', type: 'privacy'},
  {name: 'Conditions d\'utilisation', type: 'terms'}
])

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({behavior: 'smooth'})
  }
}

const scrollToTop = () => {
  window.scrollTo({top: 0, behavior: 'smooth'})
}

const handleScroll = () => {
  showBackToTop.value = window.scrollY > 300
}

const subscribeNewsletter = async () => {
  isSubscribing.value = true

  try {
    // Simulate API call
    await new Promise(resolve => setTimeout(resolve, 1000))
    console.log('Newsletter subscription:', newsletterEmail.value)
    newsletterEmail.value = ''
    // You could show a success message here
  } catch (error) {
    console.error('Newsletter subscription error:', error)
  } finally {
    isSubscribing.value = false
  }
}

const showLegalModal = (type) => {
  const content = {
    legal: {
      title: 'Mentions légales',
      content: 'Informations légales concernant ce site web...'
    },
    privacy: {
      title: 'Politique de confidentialité',
      content: 'Politique concernant la protection de vos données personnelles...'
    },
    terms: {
      title: 'Conditions d\'utilisation',
      content: 'Conditions d\'utilisation de ce site web...'
    }
  }

  modalContent.value = content[type]
  showModal.value = true
}

const closeModal = () => {
  showModal.value = false
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>