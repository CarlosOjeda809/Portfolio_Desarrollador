<script setup>
const menuOpen = ref(false)

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value
}
</script>

<template>
  <main
    class="flex flex-grow flex-col items-center w-full
           px-4 py-30          sm:px-8 sm:py-12   md:px-16 md:py-24   lg:p-40             justify-center z-10"
    >
    <div
      class="w-full max-w-3xl lg:max-w-4xl border-2 border-gray-400/50 bg-gray-50/40 backdrop-blur-lg rounded-xl shadow-xl p-8 sm:p-10 md:p-12 flex flex-col items-center"
    >
      <h1 class="text-3xl sm:text-4xl md:text-5xl font-bold text-black mb-8 text-center">
        ¡Hola, soy <span class="text-purple-800">Carlos Ojeda</span>!
      </h1>

      <p class="text-lg sm:text-xl mb-6 text-gray-500 leading-relaxed text-center">
        Soy un <span class="font-semibold text-purple-800">desarrollador junior</span> apasionado por la creación de <span class="font-bold">aplicaciones web y móviles</span>. Mi objetivo es
        combinar diseño y funcionalidad para crear experiencias digitales excepcionales.
      </p>

      <p class="text-lg sm:text-xl mb-10 text-gray-500 leading-relaxed text-center">
        Comencé mi viaje en el desarrollo hace 2 años, y desde entonces he estado constantemente aprendiendo
        y mejorando mis habilidades. Me especializo en varias <span class="text-purple-800 font-semibold">tecnologías frontend</span> como <span class="font-bold">Vue.js, React o
        Angular</span>. También tengo <span class="text-purple-800 font-semibold">experiencia en backend</span> con frameworks como <span class="font-bold">Node.js o Express</span>, junto a <span class="text-purple-800 font-semibold">bases
        de datos</span> como <span class="font-bold">MongoDB, MySQL o Supabase.</span>
        Actualmente, estoy buscando una oportunidad para aplicar mis conocimientos y crecer profesionalmente
        en un entorno dinámico y colaborativo sin objetivos salariales.
      </p>

      <hr class="border-gray-400/30 mb-8 w-full">

      <div class="flex items-center justify-center space-x-4 sm:space-x-6 w-full">
        <a href="https://www.linkedin.com/in/carlos-ojeda-tejerina-41061a334/" target="_blank" rel="noopener noreferrer"
          aria-label="LinkedIn" class="text-gray-500 hover:text-blue-400 transition-colors duration-500">
          <Icon name="lineicons:linkedin-original" class="w-7 h-7" />
        </a>
        <a href="https://github.com/CarlosOjeda809" target="_blank" rel="noopener noreferrer" aria-label="GitHub"
          class="text-gray-500 hover:text-gray-900 transition-colors duration-500">
          <Icon name="lineicons:github-original" class="w-7 h-7" />
        </a>
        <a href="https://x.com/PlayerCot" target="_blank" aria-label="Twitter/X"
          class="text-gray-500 hover:text-black transition-colors duration-500">
          <Icon name="fa6-brands:x-twitter" class="w-7 h-7"></Icon>
        </a>
      </div>
    </div>
  </main>
</template>