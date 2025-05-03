<script setup>
const menuOpen = ref(false)

const toggleMenu = () => {
    menuOpen.value = !menuOpen.value
}
</script>

<template>
    <main class="pt-16 sm:pt-18 pb-20 px-6 sm:px-10">
      <section class="py-10">
        <h2 class="text-6xl font-bold mt-5 p-4 rounded-md shadow-md border text-center border-gray-400/50 text-black mb-10">
          Mis Proyectos
        </h2>
  
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
  
          <div class="bg-gray-300/40 backdrop-blur-md rounded-lg shadow-md border-2 border-gray-800/20 p-6 flex flex-col h-full">
            <div class="flex-grow">
              <img src="/img/fotosindex/pokedexback.png" alt="Pokedex" class="w-full h-100 object-cover rounded-md mb-4 hover:scale-102 cursor-pointer transition-transform duration-300">
              <h3 class="text-xl font-semibold text-purple-400 mb-2">Pokedex</h3>
              <p class="text-gray-700 mb-4">Consulta rápida y sencilla de datos Pokémon mediante una API pública. El backend, desarrollado en Node.js, aplica filtrados eficientes para que la interfaz Vue.js, construida con Nuxt, muestre resultados relevantes al instante.</p>
            </div>
            <div class="mt-auto">
              <div class="flex flex-wrap gap-2 mb-3">
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">HTML5</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">CSS3</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">JavaScript</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Vue</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Nuxt</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">TailwindCSS</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Node.js</span>
              </div>
              <div class="flex justify-start space-x-2">
                <a href="https://pokedex-vue-chi-eight.vercel.app" target="_blank">
                  <button class="bg-purple-500 cursor-pointer hover:-translate-y-0.5 hover:shadow-xl hover:bg-purple-600 text-white font-bold py-2 px-4 rounded-full text-sm">Ver Demo</button>
                </a>
                <a href="https://github.com/CarlosOjeda809/PokedexVue" target="_blank">
                  <button class="bg-gray-700 cursor-pointer hover:bg-gray-600 hover:-translate-y-0.5 hover:shadow-xl text-white font-bold py-2 px-4 rounded-full text-sm">Ver Código</button>
                </a>
              </div>
            </div>
          </div>
  
          <div class="bg-gray-300/40 backdrop-blur-md rounded-lg shadow-md p-6 border-2 border-gray-800/20 flex flex-col h-full">
            <div class="flex-grow">
              <img src="https://img.freepik.com/fotos-premium/violin_553012-48447.jpg" alt="Instruments" class="w-full h-100 object-cover rounded-md mb-4 hover:scale-102 cursor-pointer transition-transform duration-300">
              <h3 class="text-xl font-semibold text-purple-400 mb-2">Instruments</h3>
              <p class="text-gray-700 mb-4">Sitio web interactivo con funcionalidades CRUD completas para la administración de datos almacenados en una base de datos. Incorpora un sistema de autenticación de usuarios para un acceso seguro y gestiona eficientemente las llaves foráneas, manteniendo la integridad y las relaciones entre los datos.</p>
            </div>
            <div class="mt-auto">
              <div class="flex flex-wrap gap-2 mb-3">
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">HTML5</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">CSS3</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">JavaScript</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Vue</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Nuxt</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">TailwindCSS</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Supabase</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Node.js</span>
              </div>
              <div class="flex justify-start space-x-2">
                <a href="https://instruments-work.vercel.app" target="_blank">
                  <button class="bg-purple-500 cursor-pointer hover:-translate-y-0.5 hover:shadow-xl hover:bg-purple-600 text-white font-bold py-2 px-4 rounded-full text-sm">Ver Demo</button>
                </a>
                <a href="https://github.com/CarlosOjeda809/InstrumentsVue" target="_blank">
                  <button class="bg-gray-700 cursor-pointer hover:-translate-y-0.5 hover:shadow-xl hover:bg-gray-600 text-white font-bold py-2 px-4 rounded-full text-sm">Ver Código</button>
                </a>
              </div>
            </div>
          </div>
  
          <div class="bg-gray-300/40 backdrop-blur-md rounded-lg shadow-md border-2 border-gray-800/20 p-6 flex flex-col h-full">
            <div class="flex-grow">
              <img src="https://imagenes.noticiasrcn.com/cms/2024/09/07160917/series-fav.webp?w=480" alt="Series" class="w-full h-100 object-cover rounded-md mb-4 hover:scale-102 cursor-pointer transition-transform duration-300">
              <h3 class="text-xl font-semibold text-purple-400 mb-2">Series</h3>
              <p class="text-gray-700 mb-4">Web de sistema CRUD conectada a una base de datos realizada en MongoDB, que permite gestionar los datos y mostrarlos en directo. Al modificar la API, la app de Ionic también actualiza la información al instante pues recibe datos de esta.</p>
            </div>
            <div class="mt-auto">
              <div class="flex flex-wrap gap-2 mb-3">
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">HTML5</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">CSS3</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">JavaScript</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Ionic</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Angular</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">MongoDB</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Webstorm</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Bootstrap</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">NestJS</span>
              </div>
              <div class="flex justify-start space-x-2">
                <button class="bg-purple-500 hover:-translate-y-0.5 hover:shadow-xl hover:bg-purple-600 text-white font-bold py-2 px-4 rounded-full text-sm">En proceso de deploy</button>
                <a href="https://github.com/CarlosOjeda809/Series-Project" target="_blank">
                  <button class="bg-gray-700 cursor-pointer hover:-translate-y-0.5 hover:shadow-xl hover:bg-gray-600 text-white font-bold py-2 px-4 rounded-full text-sm">Ver Código</button>
                </a>
              </div>
            </div>
          </div>
  
          <div class="bg-gray-300/40 backdrop-blur-md rounded-lg border-2 border-gray-800/20 shadow-md p-6 flex flex-col h-full">
            <div class="flex-grow">
              <img src="https://img.freepik.com/fotos-premium/multitud-personas-banderas-manifestacion-protesta-red-neuronal-generada-ia_76080-49863.jpg" alt="Agora" class="w-full h-auto object-cover rounded-md mb-4 hover:scale-102 cursor-pointer transition-transform duration-300">
              <h3 class="text-xl font-semibold text-purple-400 mb-2">Agora</h3>
              <p class="text-gray-700 mb-4">APP / WEB que permite la creación de foros y manifestaciones a tiempo real. Contiene gestión de usuarios y una interfaz de mensajes para facilitar la comunicación.</p>
            </div>
            <div class="mt-auto">
              <div class="flex flex-wrap gap-2 mb-3">
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">HTML5</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">CSS3</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">JavaScript</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Vue</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Nuxt</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">TailwindCSS</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Supabase</span>
                <span class="inline-block bg-gray-700 rounded-full px-3 py-1 text-sm font-semibold text-gray-300">Node.js</span>
              </div>
              <div class="flex justify-start space-x-2">
                <button class="bg-purple-500 cursor-pointer hover:-translate-y-0.5 hover:shadow-xl hover:bg-purple-600 text-white font-bold py-2 px-4 rounded-full text-sm">Ver Demo</button>
                <button class="bg-gray-700 hover:bg-gray-600 cursor-pointer hover:-translate-y-0.5 hover:shadow-xl text-white font-bold py-2 px-4 rounded-full text-sm">Ver Código</button>
              </div>
            </div>
          </div>
  
        </div>
     </section>
    </main>
  </template>