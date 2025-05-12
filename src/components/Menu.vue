<template>
  <section id="top">
    <div id="logo" class="logo">
      <b style="color: white; font-size: 1.3em"
        >am | <b style="color: var(--theme-color)">brisolla</b></b
      >
    </div>
    <div class="menu">
      <ul>
        <li v-for="(item, index) in Menu" :key="index">
          <a class="menu-link" :href="item.path"
            >{{ item.name[activeLang] }}
            <div class="link-line"></div
          ></a>
        </li>
      </ul>
    </div>
    <div class="social">

      <div class="langs">
        <a class='lang active' @click="changeLang" lang='pt-BR'>pt-BR</a>
        <a class='lang' @click="changeLang" lang='en-US'>en-US</a>
      </div>
    


      <a href="https://github.com/ambrisolla" target="_blank"
        ><i class="fab fa-github"></i
      ></a>
      <a href="https://www.linkedin.com/in/brisolla/" target="_blank"
        ><i class="fab fa-linkedin"></i
      ></a>
      <a href="https://instagram.com/andrebrisolla" target="_blank"
        ><i class="fab fa-instagram"></i
      ></a>
    </div>
    <div class="mobile-menu" @click="mobileMenu">
      <div class="lines">
        <div class="line"></div>
        <div class="line"></div>
      </div>
    </div>
  </section>
  <div id="overlay-mobile-menu">
    <div>
      <ul>
        <li v-for="(item, index) in menu" :key="index">
          <a class="menu-link" :href="item.link"
            >{{ item.name }}
            <div class="link-line"></div
          ></a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref, inject } from "vue";

import Menu from "../assets/menu.json";

// lang
const langs = inject('langs')
const activeLang = inject('activeLang')
function changeLang(e) {
  const langs = document.querySelectorAll(".lang");
  langs.forEach((l) => {
    l.classList.remove("active");
  });
  const newLang = e.target.getAttribute("lang");
  activeLang.value = newLang;
  e.target.classList.add("active");
}


const menu = ref([
  { name: "Home", link: "#home" },
  { name: "About", link: "#about" },
  { name: "Carrer", link: "#carrer" },
  { name: "Skills", link: "#skills" },
  { name: "Contact", link: "#contact" },
]);

onMounted(() => {
  
  if (window.location.pathname == '/') {
    document.querySelector('[href="#home"]').click();
  }

  // Alogo animate event
  const logo = document.getElementById("logo");
  logo.addEventListener("click", () => {
    document.querySelector('[href="#home"]').click();
  });

  // change link class when scroll
  const links = document.querySelectorAll(".menu-link");
  document.addEventListener('scroll', () => {
    const sections = document.querySelectorAll('section');
    let scrollPos = window.scrollY + 50;
    sections.forEach((section) => {
      if (scrollPos >= section.offsetTop && scrollPos < section.offsetTop + section.offsetHeight) {
        links.forEach((link) => link.classList.remove('active'));
        const currentLink = document.querySelector(`.menu-link[href="#${section.id}"]`);
        if (currentLink) {
          currentLink.classList.add('active');
        }
      }
    });
  });



});

// Show mobile menu
function mobileMenu() {
  const overlay = document.getElementById("overlay-mobile-menu");
  const menu = document.querySelector(".mobile-menu");
  const lines = document.querySelectorAll(".lines .line");
  if (overlay.style.display === "block") {
    overlay.style.display = "none";
    lines[0].style.transform = "rotate(0deg)";
    lines[1].style.transform = "rotate(0deg)";
    lines[1].style.marginTop = "0px";
  } else {
    overlay.style.display = "block";
    lines[0].style.transform = "rotate(45deg)";
    lines[1].style.transform = "rotate(-45deg)";
    lines[1].style.marginTop = "-8px";
  }
}
</script>


<style scoped>
.langs {
  margin-right:30px;
  font-size:0.7em;
  border:none !important;
  border-radius:5px;
  margin-bottom:2px;
  border:solid 1px rgba(255,255,255,0.1) !important;
}
.langs > .lang {
  color:rgba(255,255,255,0.6);
  transition: all 0.3s ease-in-out;
  border:none !important;
  padding:2px 10px;
  float:left;
  cursor: pointer;
}

.langs > .lang.active {
  background:rgba(255,255,255,0.1);
}
.lang:first-child {
  border-radius: 5px 0px 0px 5px;
}
.lang:last-child {
  border-radius: 0px 5px 5px 0px;
}
#top {
  position: fixed;
  width: 100vw;
  background: var(--color-background);
  height: var(--menu-height);
  z-index: 999;
  top:0px;
}
#top > div {
  float: left;
}
.logo {
  width: 300px;
  height: var(--menu-height);
  display: flex;
  justify-content: left;
  align-items: center;
  padding-left: 30px;
  cursor: pointer;
}
.logo #logo-name,
.logo #logo-middle-name {
  font-weight: bold;
  transition: 0.3s;
  border: solid 0px red;
}
.mobile-menu {
  display: none;
}
.mobile-menu .lines {
  cursor: pointer;
}
.mobile-menu .lines .line {
  width: 30px;
  height: 3px;
  background: white;
  margin: 5px auto;
  transition: all 0.3s ease-in-out;
  border-radius: 5px;
}
.menu {
  width: calc(100vw - 600px);
  text-align: center;
  display: flex;
  height: var(--menu-height);
}
.menu ul {
  list-style: none;
  padding: 0;
  float: left;
  margin: auto auto;
}
.menu ul li {
  display: inline-block;
  padding: 0;
}
.menu ul li a {
  text-decoration: none;
  color: var(--color-text);
  font-size: 1em;
  color: rgba(255, 255, 255, 0.6);
  font-weight: 300;
  margin: auto 15px;
  padding: 10px 2px;
  position: relative;
}

.menu ul li a .link-line, #overlay-mobile-menu ul li a .link-line {
  position: absolute;
  width: 100%;
  height: 2px;
  background: var(--color-text);
  bottom: 0px;
  transition: all 0.3s ease-in-out;
  left: 0px;
  bottom: -3px;
  border-radius: 10px;
  background: rgba(0, 0, 0, 0);
}
#overlay-mobile-menu ul {
  text-align: center;
  margin:auto auto;
}
#overlay-mobile-menu ul li {
  float:left;
  width:100%;
  text-align: center;
  margin-bottom:20px;
}
#overlay-mobile-menu ul li a {
  padding-bottom:30px;
  
  text-align: center;
}

.menu ul li a:hover {
  color: var(--color-text-hover);
}
.menu ul li a.active, #overlay-mobile-menu ul li a.active {
  color: white;
}
.menu ul li a.active .link-line, #overlay-mobile-menu ul li a.active .link-line {
  background: var(--theme-color);
}

#overlay-mobile-menu ul li a.active .link-line {
  background: var(--theme-color);
  bottom:10px;
}

.social {
  width: 300px;
  height: var(--menu-height);
  display: flex;
  justify-content: right;
  align-items: center;
  padding-right: 30px;
}
.social i {
  color: rgba(255, 255, 255, 0.6);
  font-size: 1.5em;
  margin: 0px 10px;
  transition: all 0.3s ease-in-out;
}
.social i:hover {
  cursor: pointer;
}
.social i.fa-github:hover {
  color: white;
}
.social i.fa-linkedin:hover {
  color: #0077b5;
}
.social i.fa-instagram:hover {
  color: #e1306c;
}

#overlay-mobile-menu {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.9);
  z-index: 100;
}
#overlay-mobile-menu > div {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
#overlay-mobile-menu ul {
  list-style: none;
  padding: 0;
}
#overlay-mobile-menu ul li {
  display: block;
  padding: 0;
}
#overlay-mobile-menu ul li a {
  text-decoration: none;
  color: var(--color-text);
  font-size: 1.5em;
  color: rgba(255, 255, 255, 0.6);
  font-weight: 300;
  margin: auto auto;
  padding: 10px 2px;
  position: relative;
}

@media only screen and (max-width: 1280px) {
  .menu,
  .social {
    display: none;
  }
  .mobile-menu {
    width: calc(100vw - 300px);
    display: block;
    display: flex;
    height: var(--menu-height);
    justify-content: right;
    align-items: center;
    padding-right: 30px;
    background: none;
  }
  #top {
    background: none;
  }
}
</style>