<script setup lang="ts">
import TypewriterComponent from './components/TypewriterComponent.vue'
import AboutComponent from './components/AboutComponent.vue'
</script>

<template>
  <TypewriterComponent text="Bryan Zuniga M." />
  <AboutComponent :statements="[
    { input: 'Bryan.currentLocation', return: 'San José, Costa Rica' },
    { input: 'Bryan.contactInfo', return: '[bryanzg221@gmail.com, LinkedIn]' },
    { input: 'Bryan.skills', return: '[C#, .Net, GraphQl, MS SQL Server, Git, Vue.js]' },
    { input: 'Bryan.education', return: 'Diplomado en Tecnologías de la Información, Colegio Universitario de Cartago' },
    { input: 'Bryan.interests', return: '[Software Development, Lego, Cooking, Video Games, Marvel]' }
  ]" />
</template>

<style scoped>

</style>
