<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Projects Section -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <h2 class="text-3xl font-bold text-gray-900 mb-8">Mes Projets</h2>

      <div class="space-y-6">
        <div
            v-for="project in projects"
            :key="project.id"
            class="bg-white rounded-lg shadow-md hover:shadow-lg transition-shadow duration-300 overflow-hidden"
        >
          <div class="md:flex">
            <!-- Image -->
            <div class="md:w-1/3">
              <div
                  class="h-48 md:h-full bg-gradient-to-br from-blue-200 to-blue-400 flex items-center justify-center">
                <div class="text-white text-center">
                  <div class="text-4xl mb-2">{{ project.icon }}</div>
                  <div class="text-sm opacity-75">{{ project.type }}</div>
                </div>
              </div>
            </div>

            <!-- Content -->
            <div class="md:w-2/3 p-6">
              <div class="flex justify-between items-start mb-3">
                <h3 class="text-xl font-semibold text-gray-900">{{ project.title }}</h3>
                <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium"
                      :class="getStatusClass(project.status)">
                  {{ project.status }}
                </span>
              </div>

              <p class="text-gray-600 mb-4">{{ project.description }}</p>

              <div class="flex flex-wrap gap-2 mb-4">
                <span
                    v-for="tech in project.technologies"
                    :key="tech"
                    class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-gray-100 text-gray-800"
                >
                  {{ tech }}
                </span>
              </div>

              <div class="flex space-x-4">
                <span
                    v-for="url in project.urls"
                    :key="url"
                    class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-gray-100 text-gray-800"
                >
                <a
                    v-if="url.githubUrl"
                    :href="url.githubUrl"
                    target="_blank"
                    class="inline-flex items-center px-4 py-2 border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 transition-colors"
                >
                  <svg class="w-4 h-4 mr-2" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd"
                          d="M10 0C4.477 0 0 4.484 0 10.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0110 4.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.203 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.942.359.31.678.921.678 1.856 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0020 10.017C20 4.484 15.522 0 10 0z"
                          clip-rule="evenodd"></path>
                  </svg>
                  {{ url.name }}
                </a>
                  </span>
                <a
                    v-if="project.demoUrl"
                    :href="project.demoUrl"
                    target="_blank"
                    class="inline-flex items-center px-4 py-2 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-blue-600 hover:bg-blue-700 transition-colors"
                >
                  <svg class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                          d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"></path>
                  </svg>
                  Démo
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
import {ref} from 'vue'
import Projects from "@/components/Projects.vue";

// Sample projects data
const projects = ref([
  {
    id: 1,
    title: "Application de suivie de vulnérablité CVE",
    description: "Développement et déploiement d'une application permettant le suivie de vulnérabilité sur des technologies et éditeurs logiciels",
    type: "Développement",
    icon: "☸️",
    status: "Terminé",
    technologies: ["VueJs", "ExpressJs", "MongoDB", "Mongoose", "NodeJS", "Ansible", "Jenkins"],
    urls: [
      {githubUrl: "https://github.com/maxime67/One-client", name: "Client"},
      {githubUrl: "https://github.com/maxime67/ONE-api", name: "Api"},
      {githubUrl: "https://github.com/maxime67/ONE_sync", name: "Synchronisation"}
    ],
    demoUrl:
        null
  },
  {
    id: 2,
    title:
        "Application permettant d'exposer de la documentation",
    description:
        "Application web de classification de documentation, permet d'exposer de la documentation Notion classée par catégorie",
    type:
        "Développement",
    icon:
        "🚀",
    status:
        "Terminé",
    technologies: ["VueJs", "ExpressJs", "MongoDB", "Mongoose", "NodeJS", "Ansible", "Jenkins"],
    urls: [
      {githubUrl: "https://github.com/maxime67/DOC-VUE-ADMIN", name: "Client"},
      {githubUrl: "https://github.com/maxime67/DOC-API-ADMIN", name: "Api"},
    ],
    demoUrl:
        null
  }
  ,
  {
    id: 3,
    title:
        "Outil de visualisation de prix",
    description:
        "Application web de visualisation de données financière dans l'univers d'Albion Online",
    type:
        "Développement",
    icon:
        "🔧",
    status:
        "En cours",
    technologies: ["VueJs", "ExpressJs", "MongoDB", "Mongoose", "NodeJS", "Ansible", "Jenkins"],

    urls: [
      {githubUrl: "https://github.com/maxime67/albion_market_client", name: "Client"},
      {githubUrl: "https://github.com/maxime67/albion_market_api", name: "Api"},
    ],
    demoUrl:
        null
  }
  ,
  {
    id: 4,
    title:
        "Dashboard de Monitoring React",
    description:
        "Interface de monitoring en temps réel construite avec React et D3.js. Intégration avec des APIs de métriques et alerting automatisé.",
    type:
        "Frontend",
    icon:
        "📊",
    status:
        "Planifié",
    technologies:
        ["React", "D3.js", "WebSocket", "Material-UI", "Jest"],
    githubUrl:
        null,
    demoUrl:
        null
  }
])

// Helper function for status styling
const getStatusClass = (status) => {
  switch (status) {
    case 'Terminé':
      return 'bg-green-100 text-green-800'
    case 'En cours':
      return 'bg-blue-100 text-blue-800'
    case 'Planifié':
      return 'bg-yellow-100 text-yellow-800'
    default:
      return 'bg-gray-100 text-gray-800'
  }
}
</script>