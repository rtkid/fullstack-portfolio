<template>
  <section class="portfolio section" id="portfolio">
    <h2 class="section__title">Портфолио</h2>
    <span class="section__subtitle">Недавние работы</span>

    <swiper
      class="portfolio__container container"
      :modules="modules"
      :navigation="{
        nextEl: '.swiper-button-next',
        prevEl: '.swiper-button-prev',
      }"
      :pagination="{
        el: '.swiper-pagination',
        clickable: true,
      }"
      :slidesPerView="1"
      :spaceBetween="50"
      loop
      grabCursor
      cssMode
      keyboard
    >
      <swiper-slide
        v-for="project in projects"
        :key="project.title"
        class="portfolio__content grid"
      >
        <img :src="project.img" alt="" class="portfolio__img" />

        <div class="portfolio__data">
          <h3 class="portfolio__title">{{ project.title }}</h3>
          <p class="portfolio__description">{{ project.description }}</p>
          <a
            href="#"
            class="button button--flex button--small portfolio__button"
          >
            Demo
            <i class="uil uil-arrow-right button__icon"></i>
          </a>
        </div>
      </swiper-slide>

      <template v-slot:container-end>
        <div class="swiper-button-next">
          <i class="uil uil-angle-right-b swiper-portfolio-icon"></i>
        </div>

        <div class="swiper-button-prev">
          <i class="uil uil-angle-left-b swiper-portfolio-icon"></i>
        </div>

        <div class="swiper-pagination"></div>
      </template>
    </swiper>
  </section>

  <section class="project section">
    <div class="project__bg">
      <div class="project__container container grid">
        <div class="project_data">
          <h2 class="project__title">Вы получили новый проект</h2>
          <p class="project__description">
            Свяжитесь со мной и получите 30% скидку на ваш новый проект.
          </p>
          <a href="#contact" class="button button--flex button--white">
            Контакты
            <i class="uil uil-message project__icon button__icon"></i>
          </a>
        </div>
        <img src="@/assets/img/project.png" alt="" class="project__img" />
      </div>
    </div>
  </section>
</template>

<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation, Pagination } from "swiper";

import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";

export default {
  components: {
    Swiper,
    SwiperSlide,
  },

  setup() {
    return {
      modules: [Navigation, Pagination],
    };
  },

  data() {
    return {
      projects: [
        {
          title: "Современный Сайт",
          img: require("@/assets/img/portfolio1.jpg"),
          description:
            "Веб-сайт, адаптируемый ко всем устройствам, с компонентам пользовательского интерфейса и анимированными взаимодействиями.",
        },
        {
          title: "Брэндовый дизайн",
          img: require("@/assets/img/portfolio2.jpg"),
          description:
            "Веб-сайт, адаптируемый ко всем устройствам, с компонентам пользовательского интерфейса и анимированными взаимодействиями.",
        },
        {
          title: "Онлайн магазин",
          img: require("@/assets/img/portfolio3.jpg"),
          description:
            "Веб-сайт, адаптируемый ко всем устройствам, с компонентам пользовательского интерфейса и анимированными взаимодействиями.",
        },
      ],
    };
  },
};
</script>

<style>
.portfolio__container {
  overflow: initial;
}

.portfolio__content {
  padding: 0 1.5rem;
}

.portfolio__img {
  width: 265px;
  border-radius: 0.5rem;
  justify-self: center;
}

.portfolio__title {
  font-size: var(--h3-font-size);
  margin-bottom: var(--mb-0-5);
}

.portfolio__description {
  margin-bottom: var(--mb-0-75);
}

.portfolio__button:hover .button__icon {
  transform: translateX(0.25rem);
}

.swiper-button-prev::after,
.swiper-button-next::after {
  content: "";
}

.swiper-portfolio-icon {
  font-size: 2rem;
  color: var(--first-color);
}

.swiper-button-prev {
  left: -0.5rem;
}

.swiper-button-next {
  right: -0.5rem;
}

.swiper-horizontal > .swiper-pagination-bullets {
  bottom: -2.5rem;
}

.swiper-pagination .swiper-pagination-bullet-active {
  background-color: var(--first-color);
}

.swiper-button-prev,
.swiper-button-next,
.swiper-pagination-bullet {
  outline: none;
}

.project {
  text-align: center;
}

.project__bg {
  background-color: var(--first-color-second);
  padding-top: 3rem;
}

.project__title {
  font-size: var(--h2-font-size);
  margin-bottom: var(--mb-0-75);
}

.project__description {
  margin-bottom: var(--mb-1-5);
}

.project__title,
.project__description {
  color: #fff;
}

.project__img {
  width: 232px;
  justify-self: center;
}

@media screen and (max-width: 350px) {
  .project__img {
    width: 200px;
  }
}

@media screen and (min-width: 568px) {
  .portfolio__content,
  .project__container {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media screen and (min-width: 768px) {
  .portfolio__img {
    width: 320px;
  }

  .portfolio__content {
    align-items: center;
  }

  .project {
    text-align: initial;
  }

  .project__bg {
    background: none;
  }

  .project__container {
    background: var(--first-color-second);
    border-radius: 1rem;
    padding: 3rem 2.5rem 0;
    grid-template-columns: 1fr max-content;
    column-gap: 3rem;
  }

  .project__data {
    padding-top: 0.8rem;
  }
}

@media screen and (min-width: 1024px) {
  .portfolio__content {
    column-gap: 5rem;
  }

  .swiper-portfolio-icon {
    font-size: 3.5rem;
  }

  .swiper-button-prev {
    left: -3.5rem;
  }

  .swiper-button-next {
    right: -3.5rem;
  }

  .swiper-horizontal > .swiper-pagination-bullets {
    bottom: -4.5rem;
  }
}
</style>
