<template>
  <section id="home">
    <img src="/src/assets/perfil.jpeg" alt="" />
    <h1 class="title">{{ HomeText.title[activeLang] }}</h1>
    <p class="subtitle">{{ HomeText.text[activeLang] }}</p>
    <div class="buttons">
      <v-btn class="btn-theme" variant="tonal" @click="goTo('#about')"
        >{{ HomeText.about_btn[activeLang]}}</v-btn
      >
      <v-btn class="btn-white" variant="tonal" @click="goTo('#contact')"
        >{{ HomeText.contact_btn[activeLang]}}</v-btn
      >
    </div>
  </section>
</template>

<script setup>
import HomeText from "../assets/home.json";
import { inject } from "vue";
const activeLang = inject("activeLang");

function goTo(to) {
  let link = document.querySelector("[href='" + to + "']");
  link.click();
}
</script>


<style scoped>
section {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  padding: auto 20px;
  text-align: center;
}
img {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  margin-bottom: 20px;
  border: solid 10px rgba(0, 0, 0, 0.2);
}
.title {
  color: #fff;
  font-weight: 300;
}
.subtitle {
  color: #fff;
  font-weight: 300;
}
.buttons {
  display: flex;
  gap: 20px;
  margin-top: 30px;
}
.btn-white {
  background-color: white;
  color: #333;
  border-radius: 5px;
  padding: 10px 20px;
}
.btn-theme {
  background-color: var(--theme-color);
  color: #fff;
  border-radius: 5px;
  padding: 10px 20px;
}
</style>