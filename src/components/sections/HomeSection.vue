<template>
  <main class="main">
    <section class="home section" id="home">
      <div class="home__container container grid">
        <div class="home__content grid">
          <div class="home__social">
            <a
              v-for="social in socials"
              :key="social.iconClass"
              :href="social.href"
              class="home__social-icon"
            >
              <i class="uil" :class="social.iconClass"></i>
            </a>
          </div>

          <div class="home__img">
            <svg
              class="home__blob"
              viewBox="0 0 200 187"
              xmlns="http://www.w3.org/2000/svg"
              xmlns:xlink="http://www.w3.org/1999/xlink"
            >
              <mask id="mask0" mask-type="alpha">
                <path
                  d="M190.312 36.4879C206.582 62.1187 201.309 102.826 182.328 134.186C163.346 165.547 
                     130.807 187.559 100.226 186.353C69.6454 185.297 41.0228 161.023 21.7403 129.362C2.45775 
                     97.8511 -7.48481 59.1033 6.67581 34.5279C20.9871 10.1032 59.7028 -0.149132 97.9666 
                     0.00163737C136.23 0.303176 174.193 10.857 190.312 36.4879Z"
                />
              </mask>
              <g mask="url(#mask0)">
                <path
                  d="M190.312 36.4879C206.582 62.1187 201.309 102.826 182.328 134.186C163.346 
                  165.547 130.807 187.559 100.226 186.353C69.6454 185.297 41.0228 161.023 21.7403 
                  129.362C2.45775 97.8511 -7.48481 59.1033 6.67581 34.5279C20.9871 10.1032 59.7028 
                 -0.149132 97.9666 0.00163737C136.23 0.303176 174.193 10.857 190.312 36.4879Z"
                />

                <image
                  class="home__blob-img"
                  x="12"
                  y="18"
                  href="@/assets/img/perfil.png"
                />
              </g>
            </svg>
          </div>

          <div class="home__data">
            <h1 class="home__title">Привет, Я Никита</h1>
            <h3 class="home__subtitle">Fullstack developer</h3>
            <p class="home__description">
              Высокий уровень навыков в веб дизайне и знания позволяющие
              выполнить качественно любую работу
            </p>
            <a href="#contact" class="button button--flex">
              Контакты <i class="uil uil-message button__icon"></i>
            </a>
          </div>
        </div>

        <div class="home__scroll">
          <a href="#about" class="home__scroll-button button--flex">
            <i class="uil uil-mouse-alt home__scroll-mouse"></i>
            <span class="home__scroll-name">Скрольте вниз</span>
            <i class="uil uil-arrow-down home__scroll-arrow"></i>
          </a>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  data() {
    return {
      socials: [
        { href: "https://vk.com/rt_kid", iconClass: "uil-vk-alt" },
        { href: "https://www.whatsapp.com", iconClass: "uil-whatsapp" },
        { href: "https://github.com/rtkid", iconClass: "uil-github-alt" },
      ],
    };
  },
};
</script>

<style scoped>
.home__container {
  gap: 1rem;
}

.home__content {
  grid-template-columns: 0.5fr 3fr;
  padding-top: 3.5rem;
  align-items: center;
}

.home__social {
  display: grid;
  grid-template-columns: max-content;
  row-gap: 0.75rem;
}

.home__social-icon {
  font-size: 1.25rem;
  color: var(--first-color);
}

.home__social-icon:hover {
  color: var(--first-color-alt);
}

.home__blob {
  width: 200px;
  fill: var(--first-color);
}

.home__blob-img {
  width: 170px;
}

.home__data {
  grid-column: 1/3;
}

.home__title {
  font-size: var(--big-font-size);
}

.home__subtitle {
  font-size: var(--h3-font-size);
  color: var(--text-color);
  font-weight: var(--font-medium);
  margin-bottom: var(--mb-0-75);
}

.home__description {
  margin-bottom: var(--mb-1-5);
}

.home__scroll {
  display: none;
}

.home__scroll-button {
  color: var(--first-color);
  transition: 0.3s;
}

.home__scroll-button:hover {
  transform: translateY(0.25rem);
}

.home__scroll-mouse {
  font-size: 2rem;
}

.home__scroll-name {
  font-size: var(--small-font-size);
  color: var(--title-color);
  font-weight: var(--font-medium);
  margin-right: var(--mb-0-25);
}

.home__scroll-arrow {
  font-size: 1.25rem;
}

@media screen and (max-width: 350px) {
  .home__content {
    grid-template-columns: 0.25fr 3fr;
  }

  .home__blob {
    width: 180px;
  }
}

@media screen and (min-width: 568px) {
  .home__content {
    grid-template-columns: max-content 1fr 1fr;
  }

  .home__data {
    grid-column: initial;
  }

  .home__img {
    order: 1;
    justify-self: center;
  }
}

@media screen and (min-width: 768px) {
  .main {
    padding: 0 1rem;
  }

  .home__container {
    row-gap: 5rem;
  }

  .home__content {
    padding-top: 5.5rem;
    column-gap: 2rem;
  }

  .home__blob {
    width: 270px;
  }

  .home__scroll {
    display: block;
  }

  .home__scroll-button {
    margin-left: 3rem;
  }
}

@media screen and (min-width: 1024px) {
  .main {
    padding: 0;
  }

  .home__blob {
    width: 320px;
  }

  .home__social {
    transform: translateX(-6rem);
  }
}
</style>
