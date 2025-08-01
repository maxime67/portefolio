<template>
  <section id="experience" class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <h2 class="text-4xl font-bold text-gray-900 mb-4">Mes Expériences</h2>
        <div class="w-20 h-1 bg-gradient-to-r from-blue-600 to-purple-600 rounded-full mx-auto mt-6"></div>
      </div>

      <!-- Timeline -->
      <div class="relative">
        <!-- Timeline Line -->
        <div
            class="absolute left-4 md:left-1/2 transform md:-translate-x-px top-0 bottom-0 w-0.5 bg-gradient-to-b from-blue-500 to-purple-600"></div>

        <!-- Experience Items -->
        <div class="space-y-12">
          <div
              v-for="(experience, index) in experiences"
              :key="experience.id"
              :class="[
              'relative flex items-center',
              index % 2 === 0 ? 'md:flex-row' : 'md:flex-row-reverse'
            ]"
          >
            <!-- Timeline Dot -->
            <div
                class="absolute left-4 md:left-1/2 transform -translate-x-1/2 w-8 h-8 bg-gradient-to-br from-blue-500 to-purple-600 rounded-full border-4 border-white shadow-lg z-10 flex items-center justify-center">
              <div class="w-2 h-2 bg-white rounded-full"></div>
            </div>

            <!-- Content Card -->
            <div
                :class="[
                'w-full md:w-5/12 ml-16 md:ml-0',
                index % 2 === 0 ? 'md:mr-8' : 'md:ml-8'
              ]"
            >
              <div
                  class="bg-white rounded-2xl shadow-lg hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 overflow-hidden group border border-gray-100">
                <!-- Header -->
                <div class="relative bg-gradient-to-br from-blue-600 to-purple-700 p-6 text-white">
                  <div class="flex items-start justify-between mb-4">
                    <div class="flex items-center space-x-4">
                      <div
                          class="w-16 h-16 bg-white/20 backdrop-blur-sm rounded-xl flex items-center justify-center text-2xl border border-white/30">
                        {{ experience.icon }}
                      </div>
                      <div>
                        <h3 class="text-xl font-bold mb-1">{{ experience.title }}</h3>
                        <p class="text-blue-100 text-sm">{{ experience.company }}</p>
                      </div>
                    </div>
                    <div class="text-right">
                      <div class="bg-white/20 backdrop-blur-sm rounded-lg px-3 py-1 border border-white/30">
                        <span class="text-sm font-medium">{{ experience.period }}</span>
                      </div>
                    </div>
                  </div>

                  <!-- Status Badge -->
                  <div class="flex items-center justify-between">
                    <span
                        :class="[
                        'inline-flex items-center px-3 py-1 rounded-full text-xs font-semibold',
                        getStatusStyle(experience.status)
                      ]"
                    >
                      <div class="w-2 h-2 rounded-full mr-2" :class="getStatusDot(experience.status)"></div>
                      {{ experience.status }}
                    </span>
                    <div class="text-blue-100 text-sm">{{ experience.location }}</div>
                  </div>

                  <!-- Decorative Elements -->
                  <div class="absolute top-0 right-0 w-32 h-32 opacity-10">
                    <div class="w-full h-full bg-white rounded-full transform translate-x-16 -translate-y-16"></div>
                  </div>
                </div>

                <!-- Content -->
                <div class="p-6">
                  <p class="text-gray-600 mb-6 leading-relaxed">
                    {{ experience.description }}
                  </p>

                  <!-- Key Achievements -->
                  <div class="mb-6">
                    <h4 class="text-sm font-semibold text-gray-700 mb-3">Réalisations clés</h4>
                    <ul class="space-y-2">
                      <li
                          v-for="achievement in experience.achievements"
                          :key="achievement"
                          class="flex items-start space-x-2 text-sm text-gray-600"
                      >
                        <svg class="w-4 h-4 text-green-500 mt-0.5 flex-shrink-0" fill="currentColor"
                             viewBox="0 0 20 20">
                          <path fill-rule="evenodd"
                                d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
                                clip-rule="evenodd"></path>
                        </svg>
                        <span>{{ achievement }}</span>
                      </li>
                    </ul>
                  </div>

                  <!-- Technologies -->
                  <div class="mb-6">
                    <h4 class="text-sm font-semibold text-gray-700 mb-3">Technologies utilisées</h4>
                    <div class="flex flex-wrap gap-2">
                      <span
                          v-for="tech in experience.technologies"
                          :key="tech"
                          class="inline-flex items-center px-3 py-1 rounded-lg text-xs font-medium bg-blue-50 text-blue-700 hover:bg-blue-100 transition-colors duration-200"
                      >
                        {{ tech }}
                      </span>
                    </div>
                  </div>

                  <!-- Context/Team Info -->
                  <div class="bg-gray-50 rounded-lg p-4">
                    <div class="grid grid-cols-2 gap-4 text-sm">
                      <div>
                        <span class="text-gray-500">Type de mission</span>
                        <div class="font-medium text-gray-900">{{ experience.type }}</div>
                      </div>
                      <div v-if="experience.teamSize">
                        <span class="text-gray-500">Équipe</span>
                        <div class="font-medium text-gray-900">{{ experience.teamSize }}</div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import {ref} from 'vue'

const experiences = ref([
  {
    id: 1,
    title: "Consultant DevOps",
    company: "Capgemini",
    period: "2024 - Présent",
    location: "Rennes, France",
    type: "Support",
    status: "En cours",
    icon: "🚀",
    description: "Conseil et support envers des directions d'applications pour la migration de leur infrastructure vers une architecture cloud, dévelopement d'infrastructure as code, intégration de cloud services.",
    achievements: [
      "Suivie de plus de 50 applications vers une architecture cloud",
      "Mise en place d'infrastructures as Code avec Ansible",
      "Intégration du déploiement dans une pipeline GitLab",
      "Intération de cloud services au sein de l'architecture",
      "Rédaction de documentation utilisateur"
    ],
    technologies: [
      "Ansible", "Terraform", "GitLab CI",
      "ELK Stack", "Hashicorp Vault", "Red Hat", "Bash", "SonarQube"
    ],
    teamSize: "4-7 personnes"
  },
  {
    id: 2,
    title: "Traitement de données",
    company: "Capgemini",
    period: "2023 - 2024",
    location: "Rennes, France",
    type: "Projet R&D",
    status: "Terminé",
    icon: "🛰️",
    description: "Au sein d'un projet à ambition recherche, traitement de données satellitaires, calcul d'indices, mise en place d'un modèle de clustering",
    achievements: [
      "Traitement de données, calcul d'indices de reflectance de lumière",
      "Utilisation de modèles de clustering",
      "Migration de traitement depuis Google Earth Engine vers du python local",
      "Rédaction de papier décrivant les méthodologies appliquées",
    ],
    technologies: [
      "Python", "NumPy", "Pandas", "Scikit-learn", "Google Earth Engine",
      "JavaScript"
    ],
    teamSize: "2-3 personnes"
  },
  {
    id: 3,
    title: "Visualisation de données cartographiques.",
    company: "Capgemini",
    period: "2023 - 2024",
    location: "Rennes, France",
    type: "Projet R&D",
    status: "Terminé",
    icon: "⚡",
    description: "Au sein d'un projet à ambition recherche, architecture et développement d'un outil de visualisation de données cartographiques.",
    achievements: [
      "Architecture N-Tier",
      "Développement d'un client VueJS utilisant Lealfet pour afficher des fond de cartes",
      "Developpement d'une API Spring boot",
      "Stockage, conversion et traiement de données SIG"
    ],
    technologies: [
      "MySQL", "VueJS", "Spring boot", "Leaflet"
    ],
    teamSize: "1-2 personnes"
  },
  {
    id: 4,
    title: "Outil de calcul et de gestion d'écocontribution",
    company: "La Sodise",
    period: "2020 - 2021",
    location: "Stage - Châteaulin, France",
    type: "Stage développement",
    status: "Terminé",
    icon: "🌐",
    description: "Développement en PHP natif d'un outil de calcul d'écocontribution",
    achievements: [
      "PHP",
      "Requête SQL"
    ],
    technologies: [
      "PHP", "SQL Server", "SSMS"
    ],
    teamSize: "2 personne"
  }
])

const stats = ref({
  totalExperience: 3,
  projectsDelivered: 25,
  deploymentsManaged: 150,
  technologiesMastered: 30
})

// Helper functions for styling
const getStatusStyle = (status) => {
  const styles = {
    'En cours': 'bg-blue-500/20 text-blue-200',
    'Terminé': 'bg-green-500/20 text-green-200',
    'Planifié': 'bg-yellow-500/20 text-yellow-200'
  }
  return styles[status] || 'bg-gray-500/20 text-gray-200'
}

const getStatusDot = (status) => {
  const dots = {
    'En cours': 'bg-blue-400',
    'Terminé': 'bg-green-400',
    'Planifié': 'bg-yellow-400'
  }
  return dots[status] || 'bg-gray-400'
}
</script>