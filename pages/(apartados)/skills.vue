<script setup>

import frontendJSON from '~/json/skills/frontend.json';
import backendJSON from '~/json/skills/backend.json';
import movilJSON from '~/json/skills/movil.json';
import basesdedatosJSON from '~/json/skills/basesdedatos.json';
import otrasJSON from '~/json/skills/otras.json';
import softJSON from '~/json/skills/soft.json';


</script>

<template>

    <main class="max-w-7xl mx-auto px-4 p-30 sm:px-6 lg:px-8 justify-center items-center">
        <h1 class="text-4xl font-extrabold text-purple-700 text-center mb-8">Mis SKILLS</h1>

        <!-- FRONTEND -->
        
        <section class="mb-8 bg-white/80 backdrop-blur-sm rounded-lg shadow-md border border-gray-300 p-6">
            <h2 class="text-xl font-bold text-purple-500 mb-5">{{frontendJSON.title}}</h2>
            <div class="overflow-x-auto">
                <ul class="flex space-x-6">
                    <li v-for="skill in frontendJSON.skills" :key="skill.name" class="flex flex-col items-center hover:scale-102">
                        <div class="rounded-md w-20 h-20 flex items-center justify-center">
                            <Icon :name="skill.icon" class="text-7xl"></Icon>
                        </div>
                        <p class="text-sm text-gray-600 mt-2">{{ skill.name }}</p>
                        
                    </li>
                </ul>
            </div>
        </section>

        <!-- BACKEND -->

        <section class="mb-8 bg-white/80 backdrop-blur-sm rounded-lg shadow-md border border-gray-300 p-6">
            <h2 class="text-xl font-bold text-purple-500 mb-5">{{backendJSON.title}}</h2>
            <div class="overflow-x-auto">
                <ul class="flex space-x-6">
                    <li v-for="skill in backendJSON.skills" :key="skill.name" class="flex flex-col items-center hover:scale-102">
                        <div class="rounded-md w-20 h-20 flex items-center justify-center">
                            <Icon :name="skill.icon" class="text-7xl"></Icon>
                        </div>
                        <p class="text-sm text-gray-600 mt-2">{{ skill.name }}</p>
                        
                    </li>
                </ul>
            </div>
        </section>

        <!-- DESARROLLO MÓVIL -->

        <section class="mb-8 bg-white/80 backdrop-blur-sm rounded-lg shadow-md border border-gray-300 p-6">
            <h2 class="text-xl font-bold text-purple-500 mb-5">{{movilJSON.title}}</h2>
            <div class="overflow-x-auto">
                <ul class="flex space-x-6">
                    <li v-for="skill in movilJSON.skills" :key="skill.name" class="flex flex-col items-center hover:scale-102">
                        <div class="rounded-md w-20 h-20 flex items-center justify-center">
                            <Icon :name="skill.icon" class="text-7xl"></Icon>
                        </div>
                        <p class="text-sm text-gray-600 mt-2">{{ skill.name }}</p>
                        
                    </li>
                </ul>
            </div>
        </section>

        <!-- BASES DE DATOS -->

        <section class="mb-8 bg-white/80 backdrop-blur-sm rounded-lg shadow-md border border-gray-300 p-6">
            <h2 class="text-xl font-bold text-purple-500 mb-5">{{basesdedatosJSON.title}}</h2>
            <div class="overflow-x-auto">
                <ul class="flex space-x-6">
                    <li v-for="skill in basesdedatosJSON.skills" :key="skill.name" class="flex flex-col items-center hover:scale-102">
                        <div class="rounded-md w-20 h-20 flex items-center justify-center">
                            <Icon :name="skill.icon" class="text-7xl"></Icon>
                        </div>
                        <p class="text-sm text-gray-600 mt-2">{{ skill.name }}</p>
                        
                    </li>
                </ul>
            </div>
        </section>

        <!-- OTRAS TECNOLOGÍAS -->

        <section class="mb-8 bg-white/80 backdrop-blur-sm rounded-lg shadow-md border border-gray-300 p-6">
            <h2 class="text-xl font-bold text-purple-500 mb-5">{{otrasJSON.title}}</h2>
            <div class="overflow-x-auto">
                <ul class="flex space-x-6">
                    <li v-for="skill in otrasJSON.skills" :key="skill.name" class="flex flex-col items-center hover:scale-102">
                        <div class="rounded-md w-20 h-20 flex items-center justify-center">
                            <Icon :name="skill.icon" class="text-7xl"></Icon>
                        </div>
                        <p class="text-sm text-gray-600 mt-2">{{ skill.name }}</p>
                        
                    </li>
                </ul>
            </div>
        </section>

        <!-- SOFT SKILLS -->

        <section class="mb-8 bg-white/80 backdrop-blur-sm rounded-lg shadow-md border border-gray-300 p-6">
            <h2 class="text-xl font-bold text-purple-500 mb-5">{{softJSON.title}}</h2>
            <div class="overflow-x-auto">
                <ul class="flex space-x-6">
                    <li v-for="skill in softJSON.skills" :key="skill.desc" class="flex flex-col items-center ">
                        <div class="rounded-md w-20 h-20 flex items-center justify-center">
                            <img :src="skill.image" class="text-7xl hover:scale-102"></img>
                        </div>
                        <p class="text-sm text-gray-600 mt-2">{{ skill.desc }}</p>
                        
                    </li>
                </ul>
            </div>
        </section>
    </main>

</template>
