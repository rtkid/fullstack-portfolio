<template>
  <section class="testimonial section">
    <h2 class="section__title">Отзывы</h2>
    <span class="section__subtitle">Мои клиенты говорят</span>

    <swiper
      loop
      grabCursor
      :modules="modules"
      :pagination="{
        el: '.swiper-pagination',
        clickable: true,
        dynamicBullets: true,
      }"
      :breakpoints="{ 568: { slidesPerView: 2 } }"
      :spaceBetween="50"
      class="testimonial__container container"
    >
      <swiper-slide
        v-for="testimonial in testimonials"
        :key="testimonial.clientName"
        class="testimonial__content"
      >
        <div class="testimonial__data">
          <div class="testimonial__header">
            <img :src="testimonial.img" alt="" class="testimonial__img" />

            <div>
              <h3 class="testimonial__name">{{ testimonial.clientName }}</h3>
              <span class="testimonial__client">Клиент</span>
            </div>
          </div>

          <div>
            <i class="uil uil-star testimonial__icon-star"></i>
            <i class="uil uil-star testimonial__icon-star"></i>
            <i class="uil uil-star testimonial__icon-star"></i>
            <i class="uil uil-star testimonial__icon-star"></i>
            <i class="uil uil-star testimonial__icon-star"></i>
          </div>
        </div>

        <p class="testimonial__description">{{ testimonial.description }}</p>
      </swiper-slide>

      <template v-slot:container-end>
        <div class="swiper-pagination swiper-pagination-testimonial"></div>
      </template>
    </swiper>
  </section>
</template>

<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Pagination } from "swiper";

import "swiper/css";
import "swiper/css/pagination";

export default {
  components: {
    Swiper,
    SwiperSlide,
  },

  setup() {
    return {
      modules: [Pagination],
    };
  },

  data() {
    return {
      testimonials: [
        {
          clientName: "Соня Мармеладова",
          img: require("@/assets/img/testimonial1.jpg"),
          description:
            "У меня хорошее впечатление, я выполняю свой проект со всем возможным качеством и вниманием и поддержкой 24 часа в сутки.",
        },
        {
          clientName: "Оксана Фёдоровна",
          img: require("@/assets/img/testimonial2.jpg"),
          description:
            "У меня хорошее впечатление, я выполняю свой проект со всем возможным качеством и вниманием и поддержкой 24 часа в сутки.",
        },
        {
          clientName: "Никита Александрович",
          img: require("@/assets/img/testimonial3.jpg"),
          description:
            "У меня хорошее впечатление, я выполняю свой проект со всем возможным качеством и вниманием и поддержкой 24 часа в сутки.",
        },
      ],
    };
  },
};
</script>

<style scoped>
.testimonial__data,
.testimonial__header {
  display: flex;
}

.testimonial__data {
  justify-content: space-between;
  margin-bottom: var(--mb-1);
}

.testimonial__img {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  margin-right: var(--mb-0-75);
}

.testimonial__name {
  font-size: var(--h3-font-size);
  font-weight: var(--font-medium);
}

.testimonial__client {
  font-size: var(--small-font-size);
  color: var(--text-color-light);
}

.testimonial__description {
  margin-bottom: var(--mb-2-5);
}

.testimonial__icon-start {
  color: var(--first-color);
}

.testimonial__container .swiper-pagination-testimonial {
  bottom: 0;
}

@media screen and (max-width: 350px) {
  .testimonial__data,
  .testimonial__header {
    flex-direction: column;
    align-items: center;
  }

  .testimonial__img {
    margin-right: 0;
    margin-bottom: var(--mb-0-25);
  }

  .testimonial__data,
  .testimonial__description {
    text-align: center;
  }
}
</style>
