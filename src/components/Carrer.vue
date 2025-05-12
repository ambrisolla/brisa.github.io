<template>
  <section id="carrer">
    <h1 class="section-title">// My Carrer</h1>
    <v-timeline align="start">
      <v-timeline-item
        v-for="(company, i) in companies"
        :key="i"
        :dot-color="company.color"
        size="small"
      >
        <template v-slot:opposite>
          <div :class="`pt-1 headline font-weight-bold text-${company.color}`" v-text="company.periodo"></div>
        </template>
        <div>
          <h2 :class="`mt-n1 headline font-weight-light mb-4 text-${company.color}`">
            <span style="color:white"><a :href="company.website" target="_blank">{{company.company}}</a></span><br>
            <span class="position" >{{ company.position[activeLang] }}</span>
          </h2>
          <div style="color:white;font-weight:300">
            {{ company.text[activeLang] }}
          </div>
        </div>
      </v-timeline-item>
    </v-timeline>
  </section>
</template>

<script setup>
import { ref,inject } from "vue";
import Carrer from "../assets/carrer.json";

const companies = Carrer;


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
  padding: 160px 20px;
}
a {
  color: #fff;
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}
.position {
  font-size: 0.5em;
  color: rgba(255,255,255,0.5);
}
</style>