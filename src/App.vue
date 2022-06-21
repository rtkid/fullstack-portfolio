<template>
  <nav-bar></nav-bar>
  <home-section></home-section>
  <about-section></about-section>
  <skills-section></skills-section>
  <services-section></services-section>
  <portfolio-section></portfolio-section>
  <testimonial-section></testimonial-section>
  <contact-section></contact-section>
  <my-footer></my-footer>
  <scroll-up></scroll-up>
</template>

<script>
import NavBar from "@/components/NavBar.vue";
import HomeSection from "@/components/sections/HomeSection.vue";
import AboutSection from "@/components/sections/AboutSection.vue";
import SkillsSection from "@/components/sections/SkillsSection.vue";
import ServicesSection from "@/components/sections/ServicesSection.vue";
import PortfolioSection from "@/components/sections/PortfolioSection.vue";
import TestimonialSection from "@/components/sections/TestimonialSection.vue";
import ContactSection from "@/components/sections/ContactSection.vue";
import MyFooter from "@/components/MyFooter.vue";
import ScrollUp from "@/components/ScrollUp.vue";

export default {
  name: "App",
  components: {
    NavBar,
    HomeSection,
    AboutSection,
    SkillsSection,
    ServicesSection,
    PortfolioSection,
    TestimonialSection,
    ContactSection,
    MyFooter,
    ScrollUp,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100;200;300;400;500;600;700;900&display=swap");

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

:root {
  --header-height: 3rem;

  --hue-color: 250;

  --first-color: hsl(var(--hue-color), 69%, 61%);
  --first-color-second: hsl(var(--hue-color), 69%, 61%);
  --first-color-alt: hsl(var(--hue-color), 57%, 53%);
  --first-color-lighter: hsl(var(--hue-color), 92%, 85%);
  --title-color: hsl(var(--hue-color), 8%, 15%);
  --text-color: hsl(var(--hue-color), 8%, 45%);
  --text-color-ligth: hsl(var(--hue-color), 8%, 65%);
  --input-color: hsl(var(--hue-color), 70%, 96%);
  --body-color: hsl(var(--hue-color), 60%, 99%);
  --container-color: #fff;
  --scroll-bar-color: hsl(var(--hue-color), 12%, 90%);
  --scroll-thumb-color: hsl(var(--hue-color), 12%, 80%);

  --body-font: "Roboto", sans-serif;

  --big-font-size: 2rem;
  --h1-font-size: 1.5rem;
  --h2-font-size: 1.25rem;
  --h3-font-size: 1.125rem;
  --normal-font-size: 0.938rem;
  --small-font-size: 0.813rem;
  --smaller-font-size: 0.75rem;

  --font-medium: 500;
  --font-semi-bold: 600;

  --mb-0-25: 0.25rem;
  --mb-0-5: 0.5rem;
  --mb-0-75: 0.75rem;
  --mb-1: 1rem;
  --mb-1-5: 1.5rem;
  --mb-2: 2rem;
  --mb-2-5: 2.5rem;
  --mb-3: 3rem;

  --z-tooltip: 10;
  --z-fixed: 100;
  --z-modal: 1000;
}

@media screen and (min-width: 968px) {
  :root {
    --big-font-size: 3rem;
    --h1-font-size: 2.25rem;
    --h2-font-size: 1.5rem;
    --h3-font-size: 1.25rem;
    --normal-font-size: 1rem;
    --small-font-size: 0.875rem;
    --smaller-font-size: 0.813rem;
  }
}

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

html {
  scroll-behavior: smooth;
}

body {
  line-height: 1.5;
  margin: 0 0 var(--header-height) 0;
  font-family: var(--body-font);
  font-size: var(--normal-font-size);
  background-color: var(--body-color);
  color: var(--text-color);
}

body.dark-theme {
  --first-color-second: hsl(var(--hue-color), 30%, 8%);
  --title-color: hsl(var(--hue-color), 8%, 95%);
  --text-color: hsl(var(--hue-color), 8%, 75%);
  --input-color: hsl(var(--hue-color), 29%, 16%);
  --body-color: hsl(var(--hue-color), 28%, 12%);
  --container-color: hsl(var(--hue-color), 29%, 16%);
  --scroll-bar-color: hsl(var(--hue-color), 12%, 48%);
  --scroll-thumb-color: hsl(var(--hue-color), 12%, 36%);
}

h1,
h2,
h3,
h4 {
  color: var(--title-color);
  font-weight: var(--font-semi-bold);
}

ul {
  list-style: none;
}

a {
  text-decoration: none;
}

img {
  max-width: 100%;
  height: auto;
}

.section {
  padding: 2rem 0 4rem;
}

.section__title {
  font-size: var(--h1-font-size);
}

.section__subtitle {
  display: block;
  font-size: var(--small-font-size);
  margin-bottom: var(--mb-3);
}

.section__title,
.section__subtitle {
  text-align: center;
}

.container {
  max-width: 768px;
  margin-left: var(--mb-1-5);
  margin-right: var(--mb-1-5);
}

.grid {
  display: grid;
  gap: 1.5rem;
}

.button {
  display: inline-block;
  background-color: var(--first-color);
  color: #fff;
  padding: 0.75rem;
  border-radius: 0.5rem;
  font-weight: var(--font-medium);
}

.button:hover {
  background-color: var(--first-color-alt);
}

.button__icon {
  font-size: 1.25rem;
  margin-left: var(--mb-0-5);
  transition: 0.3s;
}

.button--white {
  background-color: #fff;
  color: var(--first-color);
}

.button--white:hover {
  background-color: #fff;
}

.button--flex {
  display: inline-flex;
  align-items: center;
}

.button--small {
  padding: 0.75rem 1rem;
}

.button--link {
  padding: 0;
  background-color: transparent;
  color: var(--first-color);
}

.button--link:hover {
  background-color: transparent;
  color: var(--first-color-alt);
}

::-webkit-scrollbar {
  width: 0.6rem;
  background-color: var(--scroll-bar-color);
  border-radius: 0.5rem;
}

::-webkit-scrollbar-thumb {
  background-color: var(--scroll-thumb-color);
}

::-webkit-scrollbar-thumb:hover {
  background-color: var(--text-color-ligth);
}

@media screen and (max-width: 350px) {
  .container {
    margin-left: var(--mb-1);
    margin-right: var(--mb-1);
  }
}

@media screen and (min-width: 768px) {
  .container {
    margin-left: auto;
    margin-right: auto;
  }

  body {
    margin: 0;
  }

  .section {
    padding: 6rem 0 2rem;
  }

  .section__subtitle {
    margin-bottom: 4rem;
  }
}

@media screen and (min-width: 1024px) {
  .container {
    max-width: 1024px;
  }
}
</style>
