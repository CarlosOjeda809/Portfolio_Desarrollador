<script setup>
import proyectosJSON from '~/json/proyectos/proyectos.json';
</script>

<template>
  <main class="pt-16 sm:pt-18 pb-20 px-6 sm:px-10">
    <section class="py-10">
      <h2 class="text-6xl font-bold mt-5 p-4 rounded-md shadow-md border text-center border-gray-400/50 text-black mb-10">Mis Proyectos</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div v-for="(project, index) in proyectosJSON" :key="index"
          class="bg-gray-300/40 backdrop-blur-md rounded-lg shadow-md border-2 border-gray-800/20 p-6 flex flex-col h-full">
          <div class="flex-grow">
            <img :src="project.image" :alt="project.title"
              class="w-full h-100 object-cover rounded-md mb-4 hover:scale-102 cursor-pointer transition-transform duration-300" />
            <h3 class="text-xl font-semibold text-purple-400 mb-2">{{ project.title }}</h3>
            <p class="text-gray-700 mb-4">{{ project.desc }}</p>
          </div>
          <div class="mt-auto">
            <div class="flex flex-wrap gap-2 mb-3">
              <span v-for="(techItem, techIndex) in project.tech" :key="techIndex"
                class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm hover:scale-103 font-semibold text-gray-300">
                {{ techItem }}
              </span>
            </div>
            <div class="flex justify-start space-x-2">
              <a v-if="project.demo" :href="project.demo" target="_blank">
                <button
                  class="bg-purple-500 cursor-pointer transition duration-400 hover:-translate-y-0.5 hover:shadow-xl hover:bg-purple-600 text-white font-bold py-2 px-4 rounded-full text-sm">
                  Ver Demo
                </button>
              </a>
              <button v-else
                class="bg-purple-300 text-white font-bold py-2 px-4 rounded-full text-sm cursor-not-allowed">
                Ver Demo
              </button>
              <a v-if="project.code" :href="project.code" target="_blank">
                <button
                  class="bg-gray-700 cursor-pointer transition duration-400 hover:bg-gray-600 hover:-translate-y-0.5 hover:shadow-xl text-white font-bold py-2 px-4 rounded-full text-sm">
                  Ver Código
                </button>
              </a>
              <button v-else class="bg-gray-500 text-white font-bold py-2 px-4 rounded-full text-sm cursor-not-allowed"
                disabled>
                Ver Código
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>