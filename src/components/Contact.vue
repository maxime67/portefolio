<template>
  <section id="contact" class="py-20 bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <h2 class="text-4xl font-bold text-gray-900 mb-4">Contactez-moi</h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto">
          Vous avez un projet ? Une opportunité ? N'hésitez pas à me contacter pour en discuter
        </p>
        <div class="w-20 h-1 bg-gradient-to-r from-blue-600 to-purple-600 rounded-full mx-auto mt-6"></div>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-3 gap-12">
        <!-- Contact Info -->
        <div class="lg:col-span-1 space-y-8">
          <!-- Contact Cards -->
          <div
              v-for="contact in contactInfo"
              :key="contact.type"
              class="bg-white rounded-xl shadow-lg p-6 hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-1 group"
          >
            <div class="flex items-center space-x-4">
              <div class="w-14 h-14 bg-gradient-to-br from-blue-500 to-purple-600 rounded-xl flex items-center justify-center text-white text-xl group-hover:scale-110 transition-transform duration-300">
                {{ contact.icon }}
              </div>
              <div class="flex-1">
                <h3 class="font-bold text-gray-900 text-lg mb-1">{{ contact.type }}</h3>
                <div class="text-gray-600">
                  <a
                      v-if="contact.link"
                      :href="contact.link"
                      target="_blank"
                      rel="noopener noreferrer"
                      class="hover:text-blue-600 transition-colors duration-200 break-all"
                  >
                    {{ contact.value }}
                  </a>
                  <span v-else>{{ contact.value }}</span>
                </div>
                <p class="text-sm text-gray-500 mt-1">{{ contact.description }}</p>
              </div>
            </div>
          </div>

          <!-- Availability Status -->
          <div class="bg-gradient-to-br from-green-500 to-emerald-600 rounded-xl p-6 text-white">
            <div class="flex items-center space-x-3 mb-4">
              <div class="w-4 h-4 bg-white rounded-full animate-pulse"></div>
              <span class="font-bold text-lg">Statut : Disponible</span>
            </div>
            <p class="text-green-100 text-sm leading-relaxed">
              Ouvert aux nouvelles opportunités et collaborations.
              Temps de réponse habituel : 24-48h
            </p>
          </div>

          <!-- Social Links -->
          <div class="bg-white rounded-xl shadow-lg p-6">
            <h3 class="font-bold text-gray-900 text-lg mb-4 text-center">Retrouvez-moi sur</h3>
            <div class="grid grid-cols-2 gap-4">
              <a
                  v-for="social in socialLinks"
                  :key="social.name"
                  :href="social.url"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="flex items-center space-x-3 p-3 rounded-lg hover:bg-gray-50 transition-colors duration-200 group"
              >
                <div :class="[
                  'w-8 h-8 rounded-lg flex items-center justify-center text-white text-sm group-hover:scale-110 transition-transform duration-300',
                  social.color
                ]">
                  {{ social.icon }}
                </div>
                <span class="text-gray-700 font-medium group-hover:text-blue-600 transition-colors duration-200">
                  {{ social.name }}
                </span>
              </a>
            </div>
          </div>
        </div>

        <!-- Contact Form -->
        <div class="lg:col-span-2">
          <div class="bg-white rounded-2xl shadow-xl p-8">
            <div class="mb-8">
              <h3 class="text-2xl font-bold text-gray-900 mb-2">Envoyez-moi un message</h3>
              <p class="text-gray-600">Je vous répondrai dans les plus brefs délais</p>
            </div>

            <form @submit.prevent="submitForm" class="space-y-6">
              <!-- Name and Email Row -->
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                  <label for="name" class="block text-sm font-medium text-gray-700 mb-2">
                    Nom complet *
                  </label>
                  <input
                      id="name"
                      v-model="form.name"
                      type="text"
                      required
                      class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-all duration-200 hover:border-gray-400"
                      placeholder="Votre nom"
                  >
                </div>
                <div>
                  <label for="email" class="block text-sm font-medium text-gray-700 mb-2">
                    Email *
                  </label>
                  <input
                      id="email"
                      v-model="form.email"
                      type="email"
                      required
                      class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-all duration-200 hover:border-gray-400"
                      placeholder="votre.email@exemple.com"
                  >
                </div>
              </div>

              <!-- Company and Phone Row -->
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                  <label for="company" class="block text-sm font-medium text-gray-700 mb-2">
                    Entreprise
                  </label>
                  <input
                      id="company"
                      v-model="form.company"
                      type="text"
                      class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-all duration-200 hover:border-gray-400"
                      placeholder="Nom de votre entreprise"
                  >
                </div>
                <div>
                  <label for="phone" class="block text-sm font-medium text-gray-700 mb-2">
                    Téléphone
                  </label>
                  <input
                      id="phone"
                      v-model="form.phone"
                      type="tel"
                      class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-all duration-200 hover:border-gray-400"
                      placeholder="+33 X XX XX XX XX"
                  >
                </div>
              </div>

              <!-- Subject -->
              <div>
                <label for="subject" class="block text-sm font-medium text-gray-700 mb-2">
                  Sujet *
                </label>
                <select
                    id="subject"
                    v-model="form.subject"
                    required
                    class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-all duration-200 hover:border-gray-400"
                >
                  <option value="">Sélectionnez un sujet</option>
                  <option value="project">Nouveau projet</option>
                  <option value="collaboration">Collaboration</option>
                  <option value="job">Opportunité d'emploi</option>
                  <option value="consulting">Conseil/Consulting</option>
                  <option value="other">Autre</option>
                </select>
              </div>

              <!-- Budget Range (optional) -->
              <div v-if="form.subject === 'project' || form.subject === 'consulting'">
                <label for="budget" class="block text-sm font-medium text-gray-700 mb-2">
                  Budget estimé
                </label>
                <select
                    id="budget"
                    v-model="form.budget"
                    class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-all duration-200 hover:border-gray-400"
                >
                  <option value="">Non défini</option>
                  <option value="5k-10k">5k - 10k €</option>
                  <option value="10k-25k">10k - 25k €</option>
                  <option value="25k-50k">25k - 50k €</option>
                  <option value="50k+">50k+ €</option>
                </select>
              </div>

              <!-- Message -->
              <div>
                <label for="message" class="block text-sm font-medium text-gray-700 mb-2">
                  Message *
                </label>
                <textarea
                    id="message"
                    v-model="form.message"
                    rows="6"
                    required
                    class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-all duration-200 hover:border-gray-400 resize-none"
                    placeholder="Décrivez votre projet, vos besoins ou votre message..."
                ></textarea>
                <div class="mt-2 text-sm text-gray-500">
                  {{ form.message.length }} / 1000 caractères
                </div>
              </div>

              <!-- Submit Button -->
              <div class="pt-4">
                <button
                    type="submit"
                    :disabled="isSubmitting"
                    :class="[
                    'w-full py-4 px-6 rounded-lg font-semibold text-lg transition-all duration-300 transform hover:scale-105 focus:outline-none focus:ring-4 focus:ring-blue-300',
                    isSubmitting
                      ? 'bg-gray-400 cursor-not-allowed'
                      : 'bg-gradient-to-r from-blue-600 to-purple-600 hover:from-blue-700 hover:to-purple-700 text-white shadow-lg hover:shadow-xl'
                  ]"
                >
                  <span v-if="!isSubmitting" class="flex items-center justify-center">
                    <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"></path>
                    </svg>
                    Envoyer le message
                  </span>
                  <span v-else class="flex items-center justify-center">
                    <svg class="animate-spin -ml-1 mr-3 h-5 w-5 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                      <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                      <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                    </svg>
                    Envoi en cours...
                  </span>
                </button>
              </div>
            </form>

            <!-- Success/Error Messages -->
            <div v-if="submitStatus === 'success'" class="mt-6 p-4 bg-green-50 border border-green-200 rounded-lg">
              <div class="flex items-center">
                <svg class="w-5 h-5 text-green-500 mr-2" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"></path>
                </svg>
                <span class="text-green-800 font-medium">Message envoyé avec succès ! Je vous répondrai rapidement.</span>
              </div>
            </div>

            <div v-if="submitStatus === 'error'" class="mt-6 p-4 bg-red-50 border border-red-200 rounded-lg">
              <div class="flex items-center">
                <svg class="w-5 h-5 text-red-500 mr-2" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM8.707 7.293a1 1 0 00-1.414 1.414L8.586 10l-1.293 1.293a1 1 0 101.414 1.414L10 11.414l1.293 1.293a1 1 0 001.414-1.414L11.414 10l1.293-1.293a1 1 0 00-1.414-1.414L10 8.586 8.707 7.293z" clip-rule="evenodd"></path>
                </svg>
                <span class="text-red-800 font-medium">Erreur lors de l'envoi. Veuillez réessayer ou me contacter directement.</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive, watch } from 'vue'

const isSubmitting = ref(false)
const submitStatus = ref(null)

const form = reactive({
  name: '',
  email: '',
  company: '',
  phone: '',
  subject: '',
  budget: '',
  message: ''
})

const contactInfo = ref([
  {
    type: 'Email',
    value: 'maxime.heim@example.com',
    icon: '📧',
    link: 'mailto:maxime.heim@example.com',
    description: 'Réponse sous 24-48h'
  },
  {
    type: 'Téléphone',
    value: '+33 X XX XX XX XX',
    icon: '📱',
    link: 'tel:+33XXXXXXXXX',
    description: 'Lun - Ven, 9h - 18h'
  },
  {
    type: 'Localisation',
    value: 'Brest, Bretagne, France',
    icon: '📍',
    link: null,
    description: 'Disponible en remote'
  },
  {
    type: 'LinkedIn',
    value: 'linkedin.com/in/maxime-heim',
    icon: '💼',
    link: 'https://linkedin.com/in/maxime-heim',
    description: 'Profil professionnel'
  }
])

const socialLinks = ref([
  {
    name: 'GitHub',
    url: 'https://github.com/maxime67',
    icon: '💻',
    color: 'bg-gray-800'
  },
  {
    name: 'LinkedIn',
    url: 'https://linkedin.com/in/maxime-heim',
    icon: '💼',
    color: 'bg-blue-600'
  },
  {
    name: 'Twitter',
    url: 'https://twitter.com/maxime_heim',
    icon: '🐦',
    color: 'bg-blue-400'
  },
  {
    name: 'Email',
    url: 'mailto:maxime.heim@example.com',
    icon: '📧',
    color: 'bg-red-500'
  }
])

// Watch message length
watch(() => form.message, (newValue) => {
  if (newValue.length > 1000) {
    form.message = newValue.substring(0, 1000)
  }
})

const submitForm = async () => {
  isSubmitting.value = true
  submitStatus.value = null

  try {
    // Simulate API call
    await new Promise(resolve => setTimeout(resolve, 2000))

    // Here you would typically send the form data to your backend
    console.log('Form submitted:', form)

    // Reset form
    Object.keys(form).forEach(key => {
      form[key] = ''
    })

    submitStatus.value = 'success'
  } catch (error) {
    console.error('Error submitting form:', error)
    submitStatus.value = 'error'
  } finally {
    isSubmitting.value = false

    // Clear status after 5 seconds
    setTimeout(() => {
      submitStatus.value = null
    }, 5000)
  }
}
</script>