<template>
 {{ activeLang}}
  <Menu/>
  <Home/>
  <About/>
  <Carrer/>
  <Skills/>
  <Contact/>
</template>

<script setup>
import Menu from '@/components/Menu.vue'
import Home from '@/components/Home.vue'
import About from '@/components/About.vue'
import Carrer from '@/components/Carrer.vue'
import Skills from '@/components/Skills.vue'
import Contact from '@/components/Contact.vue'

import {provide, ref} from 'vue';

const langs =  ['pt-BR', 'en-US'];
const activeLang = ref('pt-BR');
provide('langs', langs)
provide('activeLang', activeLang)


</script>

<style>
h1.section-title {
  color: #fff;
  font-weight: 300;
  margin-bottom: 60px;
}
</style>