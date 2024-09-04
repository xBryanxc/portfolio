<script setup lang="ts">
import TypewriterComponent from './components/TypewriterComponent.vue'
import AboutComponent from './components/AboutComponent.vue'
</script>

<template>
  <div class="container">
    <TypewriterComponent text="Bryan Zuniga M." />
    <div class="about-me">
      <p>I am a technology enthusiast and a software developer. I am passionate about developing great software and continually expanding my knowledge.</p>
    </div>
    <AboutComponent :statements="[
      { input: 'Bryan.currentLocation', return: '&quot;San José, Costa Rica&quot;' },
      { input: 'Bryan.contactInfo', return: '[&quot;bryanzg221@gmail.com&quot;, &quot;LinkedIn&quot;]' },
      { input: 'Bryan.skills', return: '[&quot;C#&quot;, &quot;.Net&quot;, &quot;GraphQl&quot;, &quot;MS SQL Server&quot;, &quot;Git&quot;, &quot;Vue.js&quot;]' },
      { input: 'Bryan.education', return: '&quot;Diplomado en Tecnologías de la Información, Colegio Universitario de Cartago&quot;' },
      { input: 'Bryan.interests', return: '[&quot;Dogs&quot;, &quot;Lego&quot;, &quot;Cooking&quot;, &quot;Video Games&quot;, &quot;Marvel&quot;, &quot;Fitness&quot;]' }
  ]" />
  </div>
</template>

<style scoped>
.container {
max-width: 1000px;
margin: 0 auto;
padding: 0 40px;
}

.about-me {
margin-top: 80px;
font-size: 1.3em;
line-height: 40px;
font-family: Camphor, Open Sans, Segoe UI, sans-serif;
font-weight: 200;
color: #525f7f;
}
</style>
