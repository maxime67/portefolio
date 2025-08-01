<template>
  <section id="projects" class="py-20 bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <h2 class="text-4xl font-bold text-gray-900 mb-4">Mes Projets</h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto">
          Découvrez mes projets DevOps et développement, alliant infrastructure moderne et solutions techniques innovantes
        </p>
      </div>

      <!-- Filter Tabs -->
      <div class="flex justify-center mb-12">
        <div class="inline-flex rounded-lg border border-gray-200 bg-white p-1">
          <button
              v-for="filter in filters"
              :key="filter"
              @click="activeFilter = filter"
              :class="[
              'px-6 py-2 text-sm font-medium rounded-md transition-all duration-200',
              activeFilter === filter
                ? 'bg-blue-600 text-white shadow-sm'
                : 'text-gray-600 hover:text-gray-900 hover:bg-gray-50'
            ]"
          >
            {{ filter }}
          </button>
        </div>
      </div>

      <!-- Projects Grid -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
        <div
            v-for="project in filteredProjects"
            :key="project.id"
            class="bg-white rounded-xl shadow-lg hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 overflow-hidden group"
        >
          <!-- Project Header -->
          <div class="relative bg-gradient-to-br from-blue-600 to-purple-700 p-6 text-white">
            <div class="flex items-start justify-between">
              <div>
                <div class="text-4xl mb-2">{{ project.icon }}</div>
                <span class="inline-block px-3 py-1 bg-white/20 rounded-full text-sm font-medium">
                  {{ project.type }}
                </span>
              </div>
              <div class="flex items-center space-x-2">
                <span
                    :class="[
                    'inline-flex items-center px-3 py-1 rounded-full text-xs font-semibold',
                    getStatusStyle(project.status)
                  ]"
                >
                  <div class="w-2 h-2 rounded-full mr-2" :class="getStatusDot(project.status)"></div>
                  {{ project.status }}
                </span>
              </div>
            </div>

            <!-- Decorative elements -->
            <div class="absolute top-0 right-0 w-32 h-32 opacity-10">
              <div class="w-full h-full bg-white rounded-full transform translate-x-16 -translate-y-16"></div>
            </div>
          </div>

          <!-- Project Content -->
          <div class="p-6">
            <h3 class="text-xl font-bold text-gray-900 mb-3 group-hover:text-blue-600 transition-colors duration-200">
              {{ project.title }}
            </h3>

            <p class="text-gray-600 mb-6 leading-relaxed">
              {{ project.description }}
            </p>

            <!-- Technologies -->
            <div class="mb-6">
              <h4 class="text-sm font-semibold text-gray-700 mb-3">Technologies utilisées</h4>
              <div class="flex flex-wrap gap-2">
                <span
                    v-for="tech in project.technologies"
                    :key="tech"
                    class="inline-flex items-center px-3 py-1 rounded-lg text-xs font-medium bg-gray-100 text-gray-800 hover:bg-blue-100 hover:text-blue-800 transition-colors duration-200"
                >
                  {{ tech }}
                </span>
              </div>
            </div>

            <!-- Action Buttons -->
            <div class="flex flex-wrap gap-3">
              <a
                  v-for="url in project.urls"
                  :key="url.name"
                  :href="url.githubUrl"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="inline-flex items-center px-4 py-2 bg-gray-900 text-white rounded-lg hover:bg-gray-800 transition-all duration-200 text-sm font-medium group/btn"
              >
                <svg class="w-4 h-4 mr-2 group-hover/btn:rotate-12 transition-transform duration-200" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 0C4.477 0 0 4.484 0 10.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0110 4.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.203 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.942.359.31.678.921.678 1.856 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0020 10.017C20 4.484 15.522 0 10 0z" clip-rule="evenodd"></path>
                </svg>
                {{ url.name }}
              </a>

              <a
                  v-if="project.demoUrl"
                  :href="project.demoUrl"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="inline-flex items-center px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-all duration-200 text-sm font-medium group/demo"
              >
                <svg class="w-4 h-4 mr-2 group-hover/demo:translate-x-1 transition-transform duration-200" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"></path>
                </svg>
                Voir la démo
              </a>
            </div>
          </div>
        </div>
      </div>

      <!-- Empty State -->
      <div v-if="filteredProjects.length === 0" class="text-center py-16">
        <div class="text-6xl mb-4">🔍</div>
        <h3 class="text-xl font-semibold text-gray-900 mb-2">Aucun projet trouvé</h3>
        <p class="text-gray-600">Essayez de changer le filtre pour voir d'autres projets.</p>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const activeFilter = ref('Tous')
const filters = ['Tous', 'DevOps', 'Développement', 'Outils']

// Projects data avec des icônes plus représentatives
const projects = ref([
  {
    id: 1,
    title: "Sample de déploiement Kubernetes",
    description: "Collection de manifestes Kubernetes documentés pour la montée en compétence, incluant des exemples de déploiements, services, ConfigMaps et secrets.",
    type: "DevOps",
    icon: "⚙️",
    status: "En cours",
    technologies: ["Kubernetes", "Docker", "YAML", "kubectl", "K3S", "Manifest"],
    urls: [
      { githubUrl: "https://github.com/maxime67/manifest_k3s_sample", name: "Repo GitHub" }
    ],
    demoUrl: null
  },
  {
    id: 2,
    title: "Infrastructure as Code - Déploiement CVE Tracker",
    description: "Projet complet d'Infrastructure as Code utilisant Ansible pour automatiser le déploiement d'une stack complète (frontend Vue.js + API Express.js).",
    type: "DevOps",
    icon: "🚀",
    status: "Terminé",
    technologies: ["Ansible", "Apache"],
    urls: [
      { githubUrl: "https://github.com/maxime67/One-deploy", name: "IaC Repository" }
    ],
    demoUrl: null
  },
  {
    id: 3,
    title: "CVE Tracker",
    description: "Application full-stack pour le suivi de vulnérabilités sur des technologies et éditeurs logiciels.",
    type: "Développement",
    icon: "🛡️",
    status: "Terminé",
    technologies: ["Vue.js", "Express.js", "MongoDB", "Node.js", "Mongoose", "JWT"],
    urls: [
      { githubUrl: "https://github.com/maxime67/One-client", name: "Frontend" },
      { githubUrl: "https://github.com/maxime67/ONE-api", name: "API Backend" },
      { githubUrl: "https://github.com/maxime67/ONE_sync", name: "Data Sync" }
    ],
    demoUrl: null
  },
  {
    id: 4,
    title: "Plateforme de Documentation Technique",
    description: "Application web de classification de documentation, permet d'exposer de la documentation Notion classée par catégorie.",
    type: "Développement",
    icon: "📚",
    status: "Terminé",
    technologies: ["Vue.js", "Express.js", "MongoDB", "JWT"],
    urls: [
      { githubUrl: "https://github.com/maxime67/DOC-VUE-ADMIN", name: "Client" },
      { githubUrl: "https://github.com/maxime67/DOC-API-ADMIN", name: "API" }
    ],
    demoUrl: null
  },
  {
    id: 5,
    title: "Outil de visualisation de prix",
    description: "Application web de visualisation de données financière dans l'univers d'Albion Online",
    type: "Développement",
    icon: "📊",
    status: "En cours",
    technologies: ["Vue.js", "Express.js", "Chart.js"],
    urls: [
      { githubUrl: "https://github.com/maxime67/albion_market_client", name: "Dashboard" },
      { githubUrl: "https://github.com/maxime67/albion_market_api", name: "API" }
    ],
    demoUrl: null
  },
  {
    id: 6,
    title: "Océrisation et extraction de données provenant d'images",
    description: "Pipeline de traitement d'images automatisé utilisant Tesseract OCR et OpenAI API pour l'extraction et le stockage de données.",
    type: "Outils",
    icon: "🤖",
    status: "Terminé",
    technologies: ["Python", "Tesseract OCR", "OpenAI API", "MongoDB"],
    urls: [
      { githubUrl: "https://github.com/maxime67/img_to_text_dofus", name: "OCR Pipeline" }
    ],
    demoUrl: null
  },
  {
    id: 7,
    title: "Outils de partage d'images",
    description: "Application web Symfony pour le partage communautaire d'images correspondants à des 'build' dans le jeux escape from tarkov.",
    type: "Développement",
    icon: "🎮",
    status: "Terminé",
    technologies: ["Symfony", "Doctrine ORM", "PHP 8", "MySQL", "Twig", "Symfony/Security"],
    urls: [
      { githubUrl: "https://github.com/maxime67/modding.eft", name: "Application" }
    ],
    demoUrl: null
  }
])

// Computed property for filtering
const filteredProjects = computed(() => {
  if (activeFilter.value === 'Tous') {
    return projects.value
  }
  return projects.value.filter(project => project.type === activeFilter.value)
})

// Helper functions for styling
const getStatusStyle = (status) => {
  const styles = {
    'Terminé': 'bg-green-100 text-green-800',
    'En cours': 'bg-blue-100 text-blue-800',
    'Planifié': 'bg-yellow-100 text-yellow-800',
    'Archivé': 'bg-gray-100 text-gray-800'
  }
  return styles[status] || 'bg-gray-100 text-gray-800'
}

const getStatusDot = (status) => {
  const dots = {
    'Terminé': 'bg-green-400',
    'En cours': 'bg-blue-400',
    'Planifié': 'bg-yellow-400',
    'Archivé': 'bg-gray-400'
  }
  return dots[status] || 'bg-gray-400'
}
</script>