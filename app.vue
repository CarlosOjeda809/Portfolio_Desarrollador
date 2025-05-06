<script setup>
import Navbar from './pages/navbar.vue'
import Footer from './pages/footer.vue'

</script>

<template>
  <div class="app-container">
    <CanvasBackground />
    <div class="content-wrapper">
      <Navbar />
      <NuxtPage />
      <Footer />
      <NuxtRouteAnnouncer />
    </div>
  </div>
</template>

<style>
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  overflow-x: hidden;
}


.content-wrapper {
  position: relative;
  z-index: 1; 
}
</style>