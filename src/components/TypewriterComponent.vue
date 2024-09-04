<script setup lang="ts">
import { ref, onMounted } from 'vue';

interface TypewriterProps {
  text?: string;
  minTypeSpeed?: number;
  maxTypeSpeed?: number;
  initDelay?: number;
}

const props = withDefaults(defineProps<TypewriterProps>(), {
  text: 'Give me something to type!',
  minTypeSpeed: 50,
  maxTypeSpeed: 90,
  initDelay: 700
});

const displayText = ref('');

const clicketyClack = (
  text: string,
  minTypeSpeed: number,
  maxTypeSpeed: number,
  initDelay: number
) => {
  let str = '';
  let typeSpeed = 0;

  text.split('').forEach(c => {
    typeSpeed += Math.random() * (maxTypeSpeed - minTypeSpeed) + minTypeSpeed;
    setTimeout(() => {
      str += c;
      displayText.value = str;
    }, initDelay + typeSpeed);
  });
};

onMounted(() => {
  clicketyClack(
    props.text,
    props.minTypeSpeed,
    props.maxTypeSpeed,
    props.initDelay
  );
});
</script>

<template>
  <div class="hero-title">
    {{ displayText }}<span>&nbsp;</span>
  </div>
</template>

<style scoped>
.hero-title {
  padding-top: 100px;
  font-family: 'Monaco', Consolas, 'Lucida Console', monospace;
  font-size: 4.5em;
  color: #8ba6ba;
}

.hero-title:before {
  content: '> ';
}

.hero-title span {
  background-color: #8ba6ba; 
  animation: caret 1s steps(1) infinite;
}

@keyframes caret {
  50% {
    background-color: transparent;
  }
}

/* Media query para dispositivos móviles */
@media (max-width: 767px) { 
  .hero-title {
    font-size: 2.3em;
  }
}

.cursor {
  display: inline-block;
  width: 10px;
  height: 1em;
  background-color: #000;
  animation: blink 0.7s infinite;
}

@keyframes blink {
  0% { opacity: 0 }
  50% { opacity: 1 }
  100% { opacity: 0 }
}
</style>