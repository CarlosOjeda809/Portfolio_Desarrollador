<script setup lang="ts">
const currentSlide = ref(0)
const isAnimating = ref(false)
const direction = ref('right')

const sliderImages = ref([
    { id: 1, image: '/img/skills/frontend.png', title: 'WEB FRONTEND' },
    { id: 2, image: '/img/skills/backend.png', title: 'WEB BACKEND' },
    { id: 3, image: '/img/skills/movil.png', title: 'DESARROLLO MÓVIL' },
    { id: 4, image: '/img/skills/bases.png', title: 'BASES DE DATOS' },
    { id: 5, image: '/img/skills/otras.png', title: 'OTRAS TECNOLOGÍAS' },
    { id: 6, image: '/img/skills/soft.png', title: 'SOFT SKILLS' }
])


const changeSlide = (newIndex: number) => {
    if (isAnimating.value) return

    direction.value = newIndex > currentSlide.value ? 'right' : 'left'

    if (currentSlide.value === sliderImages.value.length - 1 && newIndex === 0) {
        direction.value = 'right'
    } else if (currentSlide.value === 0 && newIndex === sliderImages.value.length - 1) {
        direction.value = 'left'
    }

    isAnimating.value = true
    currentSlide.value = newIndex

    setTimeout(() => {
        isAnimating.value = false
    }, 400)
}

const nextSlide = () => {
    const nextIndex = (currentSlide.value + 1) % sliderImages.value.length
    changeSlide(nextIndex)
}

const prevSlide = () => {
    const prevIndex = (currentSlide.value - 1 + sliderImages.value.length) % sliderImages.value.length
    changeSlide(prevIndex)
}

const goToSlide = (index: number) => {
    if (index === currentSlide.value) return
    changeSlide(index)
}
</script>

<template>
     <div class="flex flex-col min-h-screen relative text-gray-300 font-sans leading-normal tracking-normal overflow-hidden">
        

        <main class="relative flex flex-col md:flex-row flex-grow items-center justify-center w-full px-3 sm:px-5 md:px-10 pt-28 pb-24">
            <div
                class="w-full max-w-2xl md:max-w-none md:w-2/3 lg:w-7/12 xl:w-7/12 border-2 border-gray-400/50 bg-gray-400/40 backdrop-blur-sm rounded-2xl shadow-xl p-4 sm:p-6 md:p-8 relative flex flex-col items-center">
                <h2
                    class="text-xl sm:text-2xl md:text-3xl font-bold bg-gray-800/30 p-3 ml-1 font-sans rounded-full text-white mb-5 sm:mb-6 text-center">
                    MIS SKILLS: {{ sliderImages[currentSlide].title }}
                </h2>
                <div class="relative rounded-xl overflow-hidden w-full h-80 sm:h-96 md:h-112 lg:h-120">
                    <Transition :name="`slide-${direction}`">
                        <div :key="currentSlide" class="slide-content absolute inset-0 w-full h-full">
                            <a target="_blank" rel="noopener noreferrer"
                                class="block w-full h-full  -translate-y-3 group focus:outline-none focus:ring-2 focus:ring-purple-400 rounded-md">
                                <img :src="sliderImages[currentSlide].image" :alt="sliderImages[currentSlide].title"
                                    class="w-full h-full object-cover cursor-pointer transition-transform duration-300 group-hover:scale-101 rounded-md" />
                            </a>
                        </div>
                    </Transition>

                    <button @click="prevSlide" :disabled="isAnimating"
                        class="absolute top-1/2 left-2 transform -translate-y-1/2 cursor-pointer bg-gray-900/50 text-white w-10 h-10 flex items-center justify-center rounded-full shadow-md hover:bg-purple-600/70 transition disabled:opacity-50 z-10">
                        <Icon name="lucide:chevron-left" class="w-6 h-6" />
                    </button>

                    <button @click="nextSlide" :disabled="isAnimating"
                        class="absolute top-1/2 right-2 transform cursor-pointer -translate-y-1/2 bg-gray-900/50 text-white w-10 h-10 flex items-center justify-center rounded-full shadow-md hover:bg-purple-600/70 transition disabled:opacity-50 z-10">
                        <Icon name="lucide:chevron-right" class="w-6 h-6" />
                    </button>

                    <div class="absolute bottom-4 left-0 right-0 flex justify-center space-x-3 z-10">
                        <button v-for="(slide, index) in sliderImages" :key="`dot-${slide.id}`"
                            @click="goToSlide(index)" :disabled="isAnimating"
                            class="w-2.5 h-2.5 rounded-full transition-all duration-300 focus:outline-none focus:ring-1 focus:ring-white"
                            :class="[
                                index === currentSlide ? 'bg-white scale-125' : 'bg-gray-400/70 hover:bg-gray-200/80',
                                isAnimating ? 'cursor-not-allowed opacity-50' : 'cursor-pointer'
                            ]"></button>
                    </div>
                </div>

                <button @click="navigateTo('/proyectos')"
                    class="bg-purple-600 hover:bg-purple-700 cursor-pointer text-white font-semibold py-3 px-6 sm:py-3.5 sm:px-8 rounded-full shadow-md mt-8 transition-colors text-base sm:text-lg focus:outline-none focus:ring-2 focus:ring-purple-500">
                    Ver Skills
                </button>

            </div>


        </main>
    </div>
</template>

<style scoped>
.slide-right-enter-active,
.slide-right-leave-active,
.slide-left-enter-active,
.slide-left-leave-active {
    transition: all 0.35s ease-in-out;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
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
</style>
