<template>
  <a href="#" class="scrollup" id="scroll-up">
    <i class="uil uil-arrow-up scrollup__icon"></i>
  </a>
</template>

<script>
export default {
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },

  unmounted() {
    window.removeEventListener("scroll", this.handleScroll);
  },

  methods: {
    handleScroll() {
      const scrollUp = document.getElementById("scroll-up");

      if (window.scrollY >= 560) scrollUp.classList.add("show-scroll");
      else scrollUp.classList.remove("show-scroll");
    },
  },
};
</script>

<style scoped>
.scrollup {
  position: fixed;
  right: 1rem;
  bottom: -20%;
  background-color: var(--first-color);
  opacity: 0.8;
  padding: 0 0.3rem;
  border-radius: 0.4rem;
  z-index: var(--z-tooltip);
  transition: 0.4s;
}

.scrollup:hover {
  background-color: var(--first-color-alt);
}

.scrollup__icon {
  font-size: 1.5rem;
  color: #fff;
}

.show-scroll {
  bottom: 5rem;
}
</style>
