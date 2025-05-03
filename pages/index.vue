<script setup>
import { ref } from 'vue';



const currentSlide = ref(0);
const isAnimating = ref(false);
const direction = ref('right');


const sliderImages = ref([
  { id: 1, image: '/img/fotosindex/pokedexback.png', title: 'POKEDEX', linkUrl: 'https://pokedex-vue-chi-eight.vercel.app' },
  { id: 2, image: '/img/fotosindex/violin.jpg', title: 'INSTRUMENTS', linkUrl: 'https://instruments-work.vercel.app' },
  { id: 3, image: '/img/fotosindex/manif.jpg', title: 'AGORA', linkUrl: 'https://github.com/CarlosOjeda809/Series-Project' }, 
  { id: 4, image: '/img/fotosindex/series.jpg', title: 'SERIES', linkUrl: 'https://github.com/CarlosOjeda809/Series-Project' }  
]);

const currentImage = ref(sliderImages.value[currentSlide.value].image);

const changeSlide = (newIndex) => {
  if (isAnimating.value) return;

  direction.value = newIndex > currentSlide.value ? 'right' : 'left';

  if (currentSlide.value === sliderImages.value.length - 1 && newIndex === 0) {
    direction.value = 'right';
  } else if (currentSlide.value === 0 && newIndex === sliderImages.value.length - 1) {
    direction.value = 'left';
  }

  isAnimating.value = true;

  
  setTimeout(() => {
    currentSlide.value = newIndex;
    
    currentImage.value = sliderImages.value[newIndex].image;

    
    setTimeout(() => {
        isAnimating.value = false;
    }, 400);
  }, 10); 
}

const nextSlide = () => {
  const nextIndex = (currentSlide.value + 1) % sliderImages.value.length;
  changeSlide(nextIndex);
}

const prevSlide = () => {
  const prevIndex = (currentSlide.value - 1 + sliderImages.value.length) % sliderImages.value.length;
  changeSlide(prevIndex);
}

const goToSlide = (index) => {
  if (index === currentSlide.value || isAnimating.value) return;
  changeSlide(index);
}

const navigateTo = (path) => {

  console.log(`Navegando a: ${path}`); 
}

</script>

<template>
  <div class="flex flex-col min-h-screen relative text-gray-300 font-sans leading-normal tracking-normal overflow-hidden">
    <main class="relative flex flex-col md:flex-row flex-grow items-center justify-center w-full px-3 sm:px-5 md:px-10 pt-28 pb-24">
      <div class="w-full max-w-md md:max-w-none md:w-1/3 flex flex-col items-center mb-12 md:mb-0 md:mr-10 lg:mr-16">
        <div class="justify-center items-center flex flex-col text-center md:text-left">
          <div class="brillo-css-sencillo">
             <img
               src="/img/fotosindex/perfil.png" alt="Carlos Ojeda"
               class="rounded-full w-32 h-32 md:w-40 md:h-40 object-cover border-4 border-gray-400/30" />
          </div>
          <h1 class="text-3xl sm:text-4xl md:text-5xl font-bold text-gray-800 mt-6 md:mt-7">Carlos Ojeda</h1>
          <div class="p-3 bg-gray-900/80 shadow-sm rounded-2xl mt-6">
              <p class="text-lg sm:text-xl text-white px-3">Desarrollador Junior APP / WEB</p>
          </div>
          <div
            class="flex flex-col sm:flex-row items-center space-y-4 sm:space-y-0 sm:space-x-5 mt-4 md:mt-5 w-full sm:w-auto">
            <button @click="navigateTo('/sobremi')"
              class="w-full sm:w-auto bg-gray-700/80 transition duration-300 cursor-pointer hover:shadow-lg hover:-translate-y-0.5 rounded-xl py-2.5 px-6 shadow-md font-semibold text-white hover:bg-purple-600/90 text-base sm:text-lg">
              SABER MÁS
            </button>
            <button @click="navigateTo('/contacto')"
              class="w-full sm:w-auto bg-gray-700/80 transition duration-300 rounded-xl cursor-pointer hover:shadow-lg hover:-translate-y-0.5 py-2.5 px-6 shadow-md font-semibold text-white hover:bg-purple-600/90 text-base sm:text-lg">
              CONTACTAR
            </button>
          </div>
        </div>
      </div>

      <div
        class="w-full max-w-2xl md:max-w-none md:w-2/3 lg:w-7/12 xl:w-7/12 bg-gray-100 border border-gray-300 backdrop-blur-md rounded-2xl shadow-xl p-4 sm:p-6 md:p-8 relative flex flex-col items-center">
         <h2
          class="text-xl sm:text-1xl md:text-2xl font-bold bg-gray-700/80 py-3 px-5 font-sans rounded-full text-white mb-5 sm:mb-6 text-center shadow-md">
          MIS PROYECTOS: {{ sliderImages[currentSlide].title }}
         </h2>
         <div class="relative rounded-xl overflow-hidden w-full h-64 sm:h-72 md:h-80 lg:h-96 shadow-inner">
           <Transition :name="`slide-${direction}`">
             <div :key="currentSlide" class="slide-content absolute inset-0 w-full h-full">
               <a :href="sliderImages[currentSlide].linkUrl || '#'" target="_blank" rel="noopener noreferrer"
                 class="block w-full h-full group focus:outline-none focus:ring-2 focus:ring-purple-400 rounded-md">
                 <img
                   :src="sliderImages[currentSlide].image" :alt="sliderImages[currentSlide].title"
                   class="w-full h-full object-cover cursor-pointer rounded-md
                          grayscale group-hover:grayscale-0  transition-all duration-500         group-hover:scale-105               "
                   />
               </a>
             </div>
           </Transition>

           <button @click="prevSlide" :disabled="isAnimating"
             class="absolute top-1/2 left-2 transform -translate-y-1/2 cursor-pointer bg-gray-800/60 text-white w-10 h-10 flex items-center justify-center rounded-full shadow-md hover:bg-purple-700/80 transition disabled:opacity-50 z-20 focus:outline-none focus:ring-2 focus:ring-white">
             <Icon name="lucide:chevron-left" class="w-6 h-6" />
           </button>
           <button @click="nextSlide" :disabled="isAnimating"
             class="absolute top-1/2 right-2 transform cursor-pointer -translate-y-1/2 bg-gray-800/60 text-white w-10 h-10 flex items-center justify-center rounded-full shadow-md hover:bg-purple-700/80 transition disabled:opacity-50 z-20 focus:outline-none focus:ring-2 focus:ring-white">
             <Icon name="lucide:chevron-right" class="w-6 h-6" />
           </button>

           <div class="absolute bottom-4 left-0 right-0 flex justify-center space-x-3 z-20">
             <button v-for="(slide, index) in sliderImages" :key="`dot-${slide.id}`" @click="goToSlide(index)"
               :disabled="isAnimating"
               class="w-2.5 h-2.5 rounded-full transition-all duration-300 focus:outline-none focus:ring-1 focus:ring-offset-1 focus:ring-offset-gray-800/50 focus:ring-purple-500"
               :class="[
                 index === currentSlide ? 'bg-purple-500 scale-125' : 'bg-gray-500/70 hover:bg-gray-400',
                 isAnimating ? 'cursor-not-allowed opacity-50' : 'cursor-pointer'
               ]">
             </button>
           </div>
         </div>

         <button @click="navigateTo('/proyectos')"
           class="bg-purple-600 hover:bg-purple-700 cursor-pointer transition duration-300 hover:-translate-y-1 hover:shadow-xl text-white font-semibold py-3 px-6 sm:py-3.5 sm:px-8 rounded-full shadow-md mt-8 text-base sm:text-lg focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-white/50 focus:ring-purple-500">
           Ver Todos los Proyectos
         </button>
      </div>
    </main>
  </div>
</template>

<style>

.slide-right-enter-active,
.slide-right-leave-active,
.slide-left-enter-active,
.slide-left-leave-active {
  transition: transform 0.4s ease-in-out, opacity 0.4s ease-in-out;
}

.slide-right-enter-from {
  transform: translateX(100%);
  opacity: 0;
}
.slide-right-leave-to {
  transform: translateX(-100%);
  opacity: 0;
}

.slide-left-enter-from {
  transform: translateX(-100%);
  opacity: 0;
}
.slide-left-leave-to {
  transform: translateX(100%);
  opacity: 0;
}


.brillo-css-sencillo img {
  border-radius: 50%;
  box-shadow: 0 0 15px rgba(255, 255, 255, 0.6), 0 0 25px rgba(168, 85, 247, 0.5);
}


</style>