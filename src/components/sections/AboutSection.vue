<template>
  <section class="about section" id="about">
    <h2 class="section__title">Обо Мне</h2>
    <span class="section__subtitle">Моё вступление</span>

    <div class="about__container container grid">
      <img src="@/assets/img/about.jpg" alt="" class="about__img" />

      <div class="about__data">
        <p class="about__description">
          Web developer, обладающий обширными знаниями и многолетним опытом,
          работающий в области веб-технологий и UI/UX дизайна, выполняющий
          качественную работу.
        </p>

        <div class="about__info">
          <div>
            <span class="about__info-title">08+</span>
            <span class="about__info-name">
              Лет
              <br />
              опыта
            </span>
          </div>
          <div>
            <span class="about__info-title">20+</span>
            <span class="about__info-name">
              Выполненных
              <br />
              проектов
            </span>
          </div>
        </div>

        <div class="about__buttons">
          <a download="" href="#" class="button button--flex">
            Скачать CV<i class="uil uil-download-alt button__icon"></i>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {};
</script>

<style scoped>
.about__img {
  width: 200px;
  border-radius: 0.5rem;
  justify-self: center;
  align-self: center;
}

.about__description {
  text-align: center;
  margin-bottom: var(--mb-2-5);
}

.about__info {
  display: flex;
  justify-content: space-evenly;
  margin-bottom: var(--mb-2-5);
}

.about__info-title {
  font-size: var(--h2-font-size);
  font-weight: var(--font-semi-bold);
  color: var(--title-color);
}

.about__info-name {
  font-size: var(--smaller-font-size);
}

.about__info-title,
.about__info-name {
  display: block;
  text-align: center;
}

.about__buttons {
  display: flex;
  justify-content: center;
}

@media screen and (min-width: 568px) {
  .about__container {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media screen and (min-width: 768px) {
  .about__container {
    column-gap: 5rem;
  }

  .about__img {
    width: 350px;
  }

  .about__description {
    text-align: initial;
  }

  .about__info {
    justify-content: space-evenly;
  }

  .about__buttons {
    justify-content: initial;
  }
}
</style>
