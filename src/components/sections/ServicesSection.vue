<template>
  <section class="services section" id="services">
    <h2 class="section__title">Услуги</h2>
    <span class="section__subtitle">Что я предлагаю</span>

    <div class="services__container container grid">
      <div
        v-for="service in services"
        :key="service.firstName"
        class="services__content"
      >
        <div>
          <i class="uil services__icon" :class="service.iconClass"></i>
          <h3 class="services__title">
            {{ service.firstName }}
            <br />
            {{ service.secondName }}
          </h3>
        </div>

        <span
          @click="service.active = true"
          class="button button--flex button--small button--link services__button"
        >
          Посмотреть больше
          <i class="uil uil-arrow-right button__icon"></i>
        </span>

        <div
          class="services__modal"
          :class="{ 'active-modal': service.active }"
        >
          <div class="services__modal-content">
            <h4 class="services__modal-title">
              {{ service.firstName }}
              <br />
              {{ service.secondName }}
            </h4>
            <i
              @click="service.active = false"
              class="uil uil-times services__modal-close"
            ></i>

            <ul class="services__modal-services grid">
              <li
                v-for="offer in service.offers"
                :key="offer.name"
                class="services__modal-service"
              >
                <i class="uil uil-check-circle services__modal-icon"></i>
                <p>{{ offer.name }}</p>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      services: [
        {
          firstName: "Ui/Ux",
          secondName: "Designer",
          iconClass: "uil-web-grid",
          active: false,
          offers: [
            { name: "Разработка пользовательского интерфейса." },
            { name: "Разработка макета веб-страницы." },
            { name: "Разработка взаимодействия элементов UX." },
            { name: "Позиционирование бренда вашей компании." },
          ],
        },
        {
          firstName: "Frontend",
          secondName: "Developer",
          iconClass: "uil-arrow",
          active: false,
          offers: [
            { name: "Разработка макета веб-страницы." },
            { name: "Создание взаимодействия элементов UX." },
            { name: "Разработка веб-страницы на Vue 3." },
          ],
        },
        {
          firstName: "Backend",
          secondName: "Developer",
          iconClass: "uil-java-script",
          active: false,
          offers: [
            { name: "Разработка RestAPI на NodeJs." },
            { name: "Использование фреймворка Express." },
            { name: "Создание документации RestAPI на Doxygen." },
          ],
        },
      ],
    };
  },
};
</script>

<style scoped>
.services__container {
  gap: 1.5rem;
  grid-template-columns: repeat(2, 1fr);
}

.services__content {
  position: relative;
  background-color: var(--container-color);
  padding: 3.5rem 0.5rem 1.25rem 1.5rem;
  border-radius: 0.25rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.15);
  transition: 0.3s;
}

.services__content:hover {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
}

.services__icon {
  display: block;
  font-size: 1.5rem;
  color: var(--first-color);
  margin-bottom: var(--mb-1);
}

.services__title {
  font-size: var(--h3-font-size);
  margin-bottom: var(--mb-1);
  font-weight: var(--font-medium);
}

.services__button {
  cursor: pointer;
  font-size: var(--small-font-size);
}

.services__button:hover .button__icon {
  transform: translateX(0.25rem);
}

.services__modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0 1rem;
  z-index: var(--z-modal);
  opacity: 0;
  visibility: hidden;
  transition: 0.3s;
}

.services__modal-content {
  position: relative;
  background-color: var(--container-color);
  padding: 1.5rem;
  border-radius: 0.5rem;
}

.services__modal-services {
  row-gap: 1rem;
}

.services__modal-service {
  display: flex;
}

.services__modal-title {
  font-size: var(--h3-font-size);
  font-weight: var(--font-medium);
  margin-bottom: var(--mb-1-5);
}

.services__modal-close {
  position: absolute;
  top: 1rem;
  right: 1rem;
  font-size: 1.5rem;
  color: var(--first-color);
  cursor: pointer;
}

.services__modal-icon {
  color: var(--first-color);
  margin-right: var(--mb-0-25);
}

.active-modal {
  opacity: 1;
  visibility: visible;
}

@media screen and (max-width: 350px) {
  .services__container {
    grid-template-columns: max-content;
    justify-content: center;
  }

  .services__content {
    padding-right: 3.5rem;
  }

  .services__modal {
    padding: 0 0.5rem;
  }
}

@media screen and (min-width: 768px) {
  .services__container {
    grid-template-columns: repeat(3, 218px);
    justify-content: center;
  }

  .services__icon {
    font-size: 2rem;
  }

  .services__content {
    padding: 6rem 0 2rem 2.5rem;
  }

  .services__modal-content {
    width: 450px;
  }
}

@media screen and (min-width: 1024px) {
  .services__container {
    grid-template-columns: repeat(3, 238px);
  }
}
</style>
