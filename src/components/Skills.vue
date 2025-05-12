<template>
  <section id="skills">
    <h1 class="section-title">// {{ skills.title[activeLang] }}</h1>
    <div>
      <template v-for="s in skills.skills" v-bind:key="s" >
        <h1 class="skill">{{ s.skill[activeLang] }}</h1>
        <div class="text" v-html="s.text[activeLang]"></div>
        <template v-for="t in s.tags[activeLang]" v-bind:key="t" >
          <v-chip color="primary" variant="tonal" size="small" style="margin-right:5px;">{{ t }}</v-chip>
        </template>
      </template>
    </div>
  </section>
</template>

<script setup>
import Skills from "../assets/skills.json";
const skills = Skills;
import { inject } from "vue";
const activeLang = inject("activeLang");

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
  padding:160px 20px;
}
.item {
  border: solid 1px red !important;
  min-width: 1000px !important;
}
p {
  color: #fff;
  font-weight: 300;
  margin-bottom: 10px;
}
.text {
  color: #fff;
  font-weight: 300 !important;
  margin-bottom: 10px;
}
.skill {
  margin-top:50px;
}
</style>