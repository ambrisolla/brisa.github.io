<template>
  <section id="contact">
    <h1 class="section-title">// {{ Contact.title[activeLang] }}</h1>
    <div>
      <p>
        {{ Contact.text[activeLang] }}
      </p>
      <div class="social">
        <a href="https://github.com/ambrisolla" target="_blank"
          ><i class="fa-brands fa-github"></i
        ></a>
        <a href="https://www.linkedin.com/in/brisolla/" target="_blank"
          ><i class="fa-brands fa-linkedin"></i
        ></a>
        <a href="https://instagram.com/andrebrisolla" target="_blank"
          ><i class="fa-brands fa-instagram"></i
        ></a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { inject } from "vue";
const activeLang = inject("activeLang");

import Contact from "../assets/contact.json";

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
  max-width: 600px;
  text-align: center;
}
.social {
  display: flex;
  gap: 60px;
  font-size: 4em;
  text-align: center;
  justify-content: center;
  align-items: center;
  margin-top: 60px;
}
.social i {
  transition: all 0.3s ease;
  cursor: pointer;
}
.social i.fa-github:hover {
  color: #fff;
}
.social i.fa-linkedin:hover {
  color: #0077b5;
}
.social i.fa-instagram:hover {
  color: #e1306c;
}
a {
  text-decoration: none;
  color: rgba(255, 255, 255, 0.6);
}
</style>