<script setup>

</script>

<template>
    <footer class="fixed bottom-0 left-0 right-0 bg-gray-200/50  p-3 z-30">
        <div class="space-x-5 sm:space-x-6 p-1 flex justify-center items-center mb-1">
            <a href="https://x.com/PlayerCot" aria-label="Twitter" target="_blank" class="text-gray-400 hover:text-gray-800 transition-colors duration-500">
                <Icon name="fa6-brands:x-twitter" class="w-5 h-5"></Icon>
            </a>
            <a href="https://www.instagram.com/_ojeda_055?igsh=NGNnZWNwbzh5bGJx" target="_blank" aria-label="Instagram" class="text-gray-400 hover:text-pink-500 transition-colors duration-500">
                <Icon name="simple-icons:instagram" class="w-5 h-5"></Icon>
            </a>
            <a href="https://www.linkedin.com/in/carlos-ojeda-tejerina-41061a334/" target="_blank" aria-label="LinkedIn" class="text-gray-400 hover:text-blue-500 transition-colors duration-500">
                <Icon name="lineicons:linkedin-original" class="w-5 h-5"></Icon>
            </a>
            <a @click="navigateTo('/contacto')"  aria-label="Email"
                class="text-gray-400 cursor-pointer hover:text-red-500 transition-colors duration-500">
                <Icon name="simple-icons:gmail" class="w-5 h-5"></Icon>
            </a>
        </div>
        <p class="text-center text-xs text-gray-500">&copy; {{ new Date().getFullYear() }} Carlos Ojeda. Todos los
            derechos reservados.</p>
    </footer>
</template>