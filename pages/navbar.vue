<script setup>

import { useMenu } from '~/composables/usemenu'

const {
  menuOpen,
  showPreviews,
  toggleMenu,
  handleMouseOver,
  handleMouseOut,
  navigateTo
} = useMenu()


</script>

<template>
  <div v-if="menuOpen" class="fixed top-0 left-0 w-full h-full bg-black/50 z-40"></div>
  <transition name="slide-menu">
    <div v-if="menuOpen"
      class="fixed top-0 right-0 w-full sm:w-72 h-full bg-gray-800/80 rounded-l-xl bg-opacity-90 shadow-lg z-50 p-6 flex flex-col justify-between items-start backdrop-blur-md">
      <div>
        <button @click="toggleMenu"
          class="absolute top-4 right-4 cursor-pointer text-white hover:text-purple-400 transition-colors mb-4">
          <Icon name="lucide:x" class="w-6 h-6" />
        </button>
        <div class="mt-16 ml-2 divide-y divide-gray-600 w-[full]">
          <div class="relative">

            <!-- INDEX -->
            <!-- INDEX -->
            <section class="relative" @mouseover="handleMouseOver('/')" @mouseout="handleMouseOut('/')">
              <NuxtLink to="/"
                class="block text-white transition duration-500 font-medium hover:-translate-x-2 hover:text-purple-400 cursor-pointer py-3 text-lg">
                Inicio
              </NuxtLink>
              <transition name="preview-fade">
                <div v-if="showPreviews['/']"
                  class="absolute right-full top-0 mr-10 w-64 bg-gray-800 rounded-md shadow-lg z-50 overflow-hidden">
                  <img src="/img/menuhover/index.png" alt="Vista previa Inicio" class="rounded">
                </div>
              </transition>
            </section>

            <!-- SOBRE MI -->
            <section class="relative" @mouseover="handleMouseOver('/sobremi')" @mouseout="handleMouseOut('/sobremi')">
              <NuxtLink to="/sobremi"
                class="block text-white transition duration-500 font-medium hover:-translate-x-2 hover:text-purple-400 cursor-pointer py-3 text-lg">
                Sobre Mí
              </NuxtLink>
              <transition name="preview-fade">
                <div v-if="showPreviews['/sobremi']"
                  class="absolute right-full top-0 mr-10 w-64 bg-gray-800 rounded-md shadow-lg z-50 overflow-hidden">
                  <img src="/img/menuhover/sobremi.png" alt="Vista previa Sobre Mí" class="rounded">
                </div>
              </transition>
            </section>

            <!-- SKILLS -->
            <section class="relative" @mouseover="handleMouseOver('/skills')" @mouseout="handleMouseOut('/skills')">
              <NuxtLink to="/skills"
                class="block text-white transition duration-500 font-medium hover:-translate-x-2 hover:text-purple-400 cursor-pointer py-3 text-lg">
                Skills
              </NuxtLink>
              <transition name="preview-fade">
                <div v-if="showPreviews['/skills']"
                  class="absolute right-full top-0 mr-10 w-64 bg-gray-800 rounded-md shadow-lg z-50 overflow-hidden">
                  <img src="/img/menuhover/skills.png" alt="Vista previa Skills" class="rounded">
                </div>
              </transition>
            </section>

            <!-- PROYECTOS -->
            <section class="relative" @mouseover="handleMouseOver('/proyectos')"
              @mouseout="handleMouseOut('/proyectos')">
              <NuxtLink to="/proyectos"
                class="block text-white transition duration-500 font-medium hover:-translate-x-2 hover:text-purple-400 cursor-pointer py-3 text-lg">
                Proyectos
              </NuxtLink>
              <transition name="preview-fade">
                <div v-if="showPreviews['/proyectos']"
                  class="absolute right-full top-0 mr-10 w-64 bg-gray-800 rounded-md shadow-lg z-50 overflow-hidden">
                  <img src="/img/menuhover/proyectos.png" alt="Vista previa Proyectos" class="rounded">
                </div>
              </transition>
            </section>

            <!-- ESTUDIOS -->
            <section class="relative" @mouseover="handleMouseOver('/estudios')" @mouseout="handleMouseOut('/estudios')">
              <NuxtLink to="/estudios"
                class="block text-white transition duration-500 font-medium hover:-translate-x-2 hover:text-purple-400 cursor-pointer py-3 text-lg">
                Estudios y Experiencia
              </NuxtLink>
              <transition name="preview-fade">
                <div v-if="showPreviews['/estudios']"
                  class="absolute right-full top-0 mr-10 w-64 bg-gray-800 rounded-md shadow-lg z-50 overflow-hidden">
                  <img src="/img/menuhover/estudios.png" alt="Vista previa Estudios y Experiencia" class="rounded">
                </div>
              </transition>
            </section>

            <!-- CONTACTO -->
            <section class="relative" @mouseover="handleMouseOver('/contacto')" @mouseout="handleMouseOut('/contacto')">
              <NuxtLink to="/contacto"
                class="block text-white transition duration-500 font-medium hover:-translate-x-2 hover:text-purple-400 cursor-pointer py-3 text-lg">
                Contacto
              </NuxtLink>
              <transition name="preview-fade">
                <div v-if="showPreviews['/contacto']"
                  class="absolute right-full top-0 mr-10 w-64 bg-gray-800 rounded-md shadow-lg z-50 overflow-hidden">
                  <img src="/img/menuhover/contacto.png" alt="Vista previa Contacto" class="rounded">
                </div>
              </transition>
            </section>

          </div>
        </div>
      </div>

      <!-- PARTE DE ABAJO MENU -->

      <div class="w-full mt-auto pt-6 border-t border-gray-200">
        <div class="flex items-center justify-center space-x-6 mb-4">
          <a href="https://www.linkedin.com/in/carlos-ojeda-tejerina-41061a334/" target="_blank"
            rel="noopener noreferrer" aria-label="LinkedIn"
            class="text-gray-300 hover:text-blue-400 transition-colors duration-500">
            <Icon name="lineicons:linkedin-original" class="w-7 h-7" />
          </a>
          <a href="https://github.com/CarlosOjeda809" target="_blank" rel="noopener noreferrer" aria-label="GitHub"
            class="text-gray-300 hover:text-white transition-colors duration-500">
            <Icon name="lineicons:github-original" class="w-7 h-7" />
          </a>
        </div>

        <a href="/cv_carlos.pdf"
          class="bg-purple-600 text-white py-2 transition duration-500 hover:shadow-md hover:-translate-y-0.5 px-4 rounded-full shadow-md hover:bg-purple-700 block w-full text-center font-medium">
          Descargar CV
        </a>
      </div>
    </div>
  </transition>

  <nav class="fixed top-0 left-0 right-0 z-40 flex bg-gray-200/50 items-center justify-between p-4 sm:p-5">
    <div @click="navigateTo('/')"
      class="font-semibold text-lg text-gray-500 hover:text-gray-700 hover:scale-102 sm:text-xl cursor-pointer flex flex-col leading-tight">
      <p>OJEDA</p>
      <p>CARLOS.com</p>
    </div>
    <div class="flex items-center space-x-3 sm:space-x-4 ">
      <a href="/cv_carlos.pdf" download title="Descargar CV"
        class="bg-gray-800/70 transition duration-500 backdrop-blur-sm text-white p-2.5 sm:p-3 hover:shadow-md hover:-translate-y-0.5 rounded-full shadow-md hover:bg-purple-500 flex items-center justify-center">
        <Icon name="lucide:download" class="w-5 h-5" />
        <p class="hidden sm:inline ml-2 text-sm font-medium ">Descargar CV</p>
      </a>
      <div class="relative ">
        <button @click="toggleMenu" aria-label="Abrir menú"
          class="bg-gray-800/70 cursor-pointer transition duration-500 backdrop-blur-sm text-white p-2.5 hover:shadow-md hover:-translate-y-0.5 sm:p-3 rounded-full shadow-md hover:bg-purple-500 focus:outline-none flex items-center justify-center">
          <Icon name="lucide:menu" class="w-5 h-5" />
        </button>
      </div>  
    </div>
  </nav>
</template>

<style scoped>
.preview-fade-enter-active,
.preview-fade-leave-active {
  transition: opacity 0.3s ease;
}

.preview-fade-enter-from,
.preview-fade-leave-to {
  opacity: 0;
}
</style>