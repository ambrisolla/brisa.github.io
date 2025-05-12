<template>
  <section id="about">
    <h1 class="section-title">// {{ About.title[activeLang] }}</h1>
    <div v-html="About.text[activeLang]"></div>
    
  </section>
</template>

<script setup>
import About from '../assets/about.json';
import { inject } from 'vue';
const activeLang = inject('activeLang')



</script>


<style scoped>
section {
  border-top: solid 1px rgba(0, 0, 0, 0.2);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  max-width: 1280px;
  margin: 0 auto;
  padding: 160px 20px;
}

p {
  color: #fff;
  font-weight: 300;
  
  text-align: justify;
  margin-bottom: 20px;
}
p.first::first-letter {
  font-size: 2em;
  font-weight: bold;
  color: var(--theme-color);
}
</style>