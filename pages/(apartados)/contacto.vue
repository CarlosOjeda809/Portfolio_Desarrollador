<script setup>
const nombre = ref('');
const email = ref('');
const asunto = ref('');
const telefonoData = ref('');
const mensaje = ref('');
const ubicacion = ref('Valencia (Valencia), España');

const enviando = ref(false);
const mensajeEstado = ref('');
const error = ref(false);

const enviarFormulario = async () => {
    try {
        enviando.value = true;
        mensajeEstado.value = 'Enviando mensaje...';
        error.value = false;

        const response = await fetch('https://formspree.io/f/mblodzqa', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({
                nombre: nombre.value,
                email: email.value,
                asunto: asunto.value,
                telefono: telefonoData.value,
                mensaje: mensaje.value,
                ubicacion: ubicacion.value
            })
        });

        if (response.ok) {
            mensajeEstado.value = 'Mensaje enviado con éxito';

            nombre.value = '';
            email.value = '';
            asunto.value = '';
            telefonoData.value = '';
            mensaje.value = '';
        } else {
            throw new Error('Error al enviar el formulario');
        }
    } catch (e) {
        error.value = true;
        mensajeEstado.value = 'Hubo un error al enviar el mensaje. Por favor, inténtalo de nuevo.';
        console.error('Error:', e);
    } finally {
        enviando.value = false;

        setTimeout(() => {
            mensajeEstado.value = '';
        }, 4000);
    }
};
</script>

<template>
    
        <main class="container mx-auto py-16 px-8 md:px-16 lg:px-32 xl:p-32">
            <section
                class="bg-gray-50/60 border-2 border-gray-400/20 backdrop-blur-lg rounded-3xl shadow-lg p-10 mt-30 relative z-10">
                <h2 class="text-4xl font-bold text-purple-600 mb-10 text-center">
                    ¡Hablemos!
                </h2>
                <form @submit.prevent="enviarFormulario"
                    class="grid sm  :grid-cols-2 gap-8 relative z-20 text-gray-700">

                    <div>
                        <label for="nombre" class="block text-gray-800 text-lg font-semibold mb-2">
                            Nombre *
                        </label>
                        <input type="text" id="nombre" v-model="nombre"
                            class="shadow-sm focus:ring-purple-500 border focus:border-purple-500 block w-full sm:text-lg border-gray-300 rounded-md py-3 px-4 text-gray-800" />
                    </div>
                    <div>
                        <label for="email" class="block text-gray-800 text-lg font-semibold mb-2">
                            Email *
                        </label>
                        <input type="email" id="email" v-model="email"
                            class="shadow-sm focus:ring-purple-500 border focus:border-purple-500 block w-full sm:text-lg border-gray-300 rounded-md py-3 px-4 text-gray-800" />
                    </div>

                    <div>
                        <label for="asunto" class="block text-gray-800 text-lg font-semibold mb-2">
                            Asunto
                        </label>
                        <input type="text" id="asunto" v-model="asunto"
                            class="shadow-sm focus:ring-purple-500 border focus:border-purple-500 block w-full sm:text-lg border-gray-300 rounded-md py-3 px-4 text-gray-800" />
                    </div>
                    <div>
                        <label for="telefono" class="block text-gray-800 text-lg font-semibold mb-2">
                            Teléfono
                        </label>
                        <input type="tel" v-model="telefonoData" id="telefono"
                            class="shadow-sm focus:ring-purple-500 border focus:border-purple-500 block w-full sm:text-lg border-gray-300 rounded-md py-3 px-4 text-gray-800" />
                    </div>
                    <div class="col-span-2">
                        <label for="mensaje" class="block text-gray-800 text-lg font-semibold mb-2">
                            Mensaje
                        </label>
                        <textarea id="mensaje" rows="5" v-model="mensaje"
                            class="shadow-sm focus:ring-purple-500 border focus:border-purple-500 block w-full sm:text-lg border-gray-300 rounded-md py-3 px-4 text-gray-800"></textarea>
                    </div>
                    <div class="col-span-2 hidden">
                        <label for="ubicacion" class="block text-gray-800 text-lg font-semibold mb-2">
                            Ubicación
                        </label>
                        <input type="text" v-model="ubicacion" id="ubicacion"
                            class="shadow-sm focus:ring-purple-500 focus:border-purple-500 block w-full sm:text-lg border-gray-300 rounded-md py-3 px-4 text-gray-800" />
                    </div>

                    <div class="col-span-2 flex justify-center">
                        <button type="submit"
                            class="inline-flex items-center cursor-pointer px-6 py-3 border border-transparent text-lg font-medium rounded-xl text-white bg-purple-500 hover:bg-purple-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-purple-500 transition-colors duration-300"
                            :disabled="enviando">
                            <div class="flex items-center">
                                {{ enviando ? 'Enviando...' : 'Enviar Mensaje' }}
                                <div v-if="!enviando" class="ml-3">
                                    <Icon name="material-symbols:send" class="text-xl mt-0.5"></Icon>
                                </div>
                            </div>
                        </button>
                    </div>
                    <div v-if="mensajeEstado" class="text-center p-4 justify-center col-span-2 rounded-md text-lg"
                        :class="error ? 'bg-red-100 text-red-700' : 'bg-green-100 text-green-700'">
                        {{ mensajeEstado }}
                    </div>
                </form>
            </section>
        </main>
    
</template>