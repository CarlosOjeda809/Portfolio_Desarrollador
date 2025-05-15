<script setup>

</script>

<template>
  <div class="flex flex-col min-h-screen relative text-gray-300 font-sans leading-normal tracking-normal overflow-hidden">
    <main class="container mx-auto py-10 px-6 md:px-12 lg:px-24 xl:px-32">
      
      <!-- Estudios y Experiencia -->
      <section class="mb-12">
        <header class="text-center mt-20 mb-6">
          <h2 class="text-5xl font-bold text-gray-800">
            <span class="text-purple-500">Estudios</span> y <span class="text-purple-500">Experiencia</span>
          </h2>
        </header>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
          <!-- Estudios -->
          <article class="text-center">
            <header>
              <hgroup>
                <h3 class="text-3xl font-bold text-gray-700 inline-block">Estudios</h3>
                <div class="mt-2 h-0.5 bg-gray-700 w-full"></div>
              </hgroup>
            </header>
            <section class="bg-gray-800 rounded-md shadow-md mt-4 p-6">
              <h4 class="text-lg font-semibold text-purple-300 mb-2">CFGS DAM</h4>
              <address class="not-italic text-sm text-gray-300 mb-1">
                Progresa Formación - Centro de FP
              </address>
              <time class="text-xs text-gray-400 block">Septiembre 2023 - Junio 2025</time>
            </section>
          </article>

          <!-- Experiencia -->
          <article class="text-center">
            <header>
              <hgroup>
                <h3 class="text-3xl font-bold text-gray-700 inline-block">Experiencia</h3>
                <div class="mt-2 h-0.5 bg-gray-700 w-full"></div>
              </hgroup>
            </header>
            <section class="bg-gray-800 rounded-md mt-4 shadow-md p-6">
              <h4 class="text-lg font-semibold text-pink-300 mb-2">Desarrollador Junior WEB</h4>
              <p class="text-sm text-gray-300 mb-1">Innoarea Projects - Contrato formativo</p>
              <time class="text-xs text-gray-400 block">Abril 2025 - Junio 2025</time>
            </section>
          </article>
        </div>
      </section>

      <!-- Certificaciones -->
      <section class="mb-12">
        <header class="text-center mb-6">
          <h2 class="text-3xl font-bold text-pink-800">CERTIFICACIONES</h2>
        </header>
        <p class="text-gray-400 text-center">Próximamente...</p>
      </section>
      
    </main>
  </div>
</template>
