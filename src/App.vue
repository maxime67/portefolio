<script setup>
import NavBar from "@/components/NavBar.vue";
import Experience from "@/components/Experience.vue";
import Projects from "@/components/Projects.vue";
import Footer from "@/components/Footer.vue";
import Hero from "@/components/Hero.vue";
</script>

<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Navigation -->
    <NavBar />

    <!-- Hero Section -->
    <Hero />

    <!-- Experience Section -->
    <Experience />

    <!-- Projects Section -->
    <Projects />

    <!-- Contact Section -->

    <!-- Footer -->
    <Footer />
  </div>
</template>

<style>
/* Global styles for smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Custom scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #f1f5f9;
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(to bottom, #3b82f6, #8b5cf6);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(to bottom, #2563eb, #7c3aed);
}

/* Prevent flash of unstyled content */
[v-cloak] {
  display: none;
}

/* Smooth transitions for all interactive elements */
* {
  transition-property: color, background-color, border-color, text-decoration-color, fill, stroke, opacity, box-shadow, transform, filter, backdrop-filter;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 200ms;
}

/* Focus styles for accessibility */
button:focus,
a:focus,
input:focus,
textarea:focus,
select:focus {
  outline: 2px solid #3b82f6;
  outline-offset: 2px;
}

/* Print styles */
@media print {
  .no-print {
    display: none !important;
  }
}

/* Animation keyframes for custom animations */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeInLeft {
  from {
    opacity: 0;
    transform: translateX(-30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes fadeInRight {
  from {
    opacity: 0;
    transform: translateX(30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

@keyframes bounce {
  0%, 20%, 53%, 80%, 100% {
    transform: translateY(0);
  }
  40%, 43% {
    transform: translateY(-30px);
  }
  70% {
    transform: translateY(-15px);
  }
  90% {
    transform: translateY(-4px);
  }
}

/* Utility classes for animations */
.animate-fade-in-up {
  animation: fadeInUp 0.6s ease-out forwards;
}

.animate-fade-in-left {
  animation: fadeInLeft 0.6s ease-out forwards;
}

.animate-fade-in-right {
  animation: fadeInRight 0.6s ease-out forwards;
}

.animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

.animate-bounce {
  animation: bounce 1s infinite;
}

/* Animation delays */
.animation-delay-100 { animation-delay: 100ms; }
.animation-delay-200 { animation-delay: 200ms; }
.animation-delay-300 { animation-delay: 300ms; }
.animation-delay-500 { animation-delay: 500ms; }
.animation-delay-700 { animation-delay: 700ms; }
.animation-delay-1000 { animation-delay: 1000ms; }

/* Custom gradient backgrounds */
.gradient-bg-1 {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.gradient-bg-2 {
  background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
}

.gradient-bg-3 {
  background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
}

/* Glass morphism effect */
.glass {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.glass-dark {
  background: rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

/* Custom shadows */
.shadow-glow {
  box-shadow: 0 0 20px rgba(59, 130, 246, 0.5);
}

.shadow-glow-purple {
  box-shadow: 0 0 20px rgba(139, 92, 246, 0.5);
}

/* Loading states */
.loading {
  position: relative;
  overflow: hidden;
}

.loading::after {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
  animation: loading 1.5s infinite;
}

@keyframes loading {
  0% { left: -100%; }
  100% { left: 100%; }
}

/* Responsive text sizes */
@media (max-width: 640px) {
  .text-responsive-xl {
    font-size: 1.5rem;
    line-height: 2rem;
  }
}

@media (min-width: 641px) {
  .text-responsive-xl {
    font-size: 2rem;
    line-height: 2.5rem;
  }
}

@media (min-width: 1024px) {
  .text-responsive-xl {
    font-size: 2.5rem;
    line-height: 3rem;
  }
}

/* Dark mode support (if needed later) */
@media (prefers-color-scheme: dark) {
  .dark-mode-auto {
    background-color: #1f2937;
    color: #f9fafb;
  }
}

/* High contrast mode support */
@media (prefers-contrast: high) {
  .high-contrast {
    border: 2px solid;
  }
}

/* Reduced motion support */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}

/* Performance optimizations */
.will-change-transform {
  will-change: transform;
}

.will-change-opacity {
  will-change: opacity;
}

/* Content visibility optimization */
.content-visibility-auto {
  content-visibility: auto;
  contain-intrinsic-size: 1000px;
}
</style>