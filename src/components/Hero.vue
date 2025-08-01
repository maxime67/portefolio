<template>
  <section class="relative min-h-screen flex items-center justify-center bg-gradient-to-br from-blue-900 via-blue-800 to-purple-900 overflow-hidden">
    <!-- Background Pattern -->
    <div class="absolute inset-0 opacity-10">
      <div class="absolute inset-0" style="background-image: radial-gradient(circle at 25% 25%, #ffffff 2px, transparent 2px), radial-gradient(circle at 75% 75%, #ffffff 2px, transparent 2px); background-size: 50px 50px;"></div>
    </div>

    <!-- Floating Elements -->
    <div class="absolute inset-0 overflow-hidden">
      <div class="absolute top-1/4 left-1/4 w-64 h-64 bg-blue-400 rounded-full mix-blend-multiply filter blur-xl opacity-20 animate-blob"></div>
      <div class="absolute top-1/3 right-1/4 w-64 h-64 bg-purple-400 rounded-full mix-blend-multiply filter blur-xl opacity-20 animate-blob animation-delay-2000"></div>
      <div class="absolute bottom-1/4 left-1/3 w-64 h-64 bg-pink-400 rounded-full mix-blend-multiply filter blur-xl opacity-20 animate-blob animation-delay-4000"></div>
    </div>

    <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
      <!-- Main Content -->
      <div class="animate-fade-in-up">
        <!-- Name and Title -->
        <h1 class="text-5xl md:text-7xl font-bold text-white mb-6 tracking-tight">
          Maxime Heim
        </h1>

        <div class="mb-8">
          <div class="inline-flex items-center space-x-2 text-xl md:text-2xl text-blue-200 mb-4">
            <span class="animate-typing">Développeur</span>
            <span class="text-blue-400">•</span>
            <span class="animate-typing animation-delay-1000">DevOps</span>
          </div>
        </div>

        <!-- Description -->
        <p class="text-xl md:text-2xl text-blue-100 max-w-4xl mx-auto mb-12 leading-relaxed">
          Passionné par l'automatisation, l'infrastructure et l'architecture.
        </p>

        <!-- Skills Tags -->
        <div class="flex flex-wrap justify-center gap-3 mb-12">
          <span
              v-for="(skill, index) in heroSkills"
              :key="skill"
              :style="{ animationDelay: `${index * 100}ms` }"
              class="inline-flex items-center px-4 py-2 bg-white/10 backdrop-blur-sm rounded-full text-white font-medium border border-white/20 hover:bg-white/20 transition-all duration-300 animate-fade-in-up transform hover:scale-105"
          >
            {{ skill }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const heroSkills = ref([
  'Kubernetes', 'Docker', 'Ansible', 'Terraform',
  'Vue.js', 'Node.js', 'Python', 'CI/CD'
])

const stats = ref({
  projects: 15,
  experience: 3,
  technologies: 25,
  deployments: 100
})

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<style scoped>
@keyframes blob {
  0% { transform: translate(0px, 0px) scale(1); }
  33% { transform: translate(30px, -50px) scale(1.1); }
  66% { transform: translate(-20px, 20px) scale(0.9); }
  100% { transform: translate(0px, 0px) scale(1); }
}

@keyframes fade-in-up {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes typing {
  from { opacity: 0; }
  to { opacity: 1; }
}

.animate-blob {
  animation: blob 7s infinite;
}

.animation-delay-2000 {
  animation-delay: 2s;
}

.animation-delay-4000 {
  animation-delay: 4s;
}

.animation-delay-1000 {
  animation-delay: 1s;
}

.animate-fade-in-up {
  animation: fade-in-up 0.8s ease-out;
}

.animate-typing {
  animation: typing 2s ease-in-out infinite alternate;
}
</style>