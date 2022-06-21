<template>
  <section class="section contact" id="contact">
    <h2 class="section__title">Контакты</h2>
    <span class="section__subtitle">Связаться</span>

    <div class="contact__container container grid">
      <div>
        <div
          v-for="contact in contacts"
          :key="contact.name"
          class="contact__information"
        >
          <i class="uil contact__icon" :class="contact.iconClass"></i>

          <div>
            <h3 class="contact__title">{{ contact.title }}</h3>
            <span class="contact__subtitle">{{ contact.subtitle }}</span>
          </div>
        </div>
      </div>

      <form action="" class="contact__form grid">
        <div class="contact__inputs grid">
          <div class="contact__content">
            <label for="" class="contact__label">Имя</label>
            <input type="text" class="contact__input" />
          </div>
          <div class="contact__content">
            <label for="" class="contact__label">Email</label>
            <input type="email" class="contact__input" />
          </div>
        </div>

        <div class="contact__content">
          <label for="" class="contact__label">Проект</label>
          <input type="text" class="contact__input" />
        </div>

        <div class="contact__content">
          <label for="" class="contact__label">Сообщение</label>
          <textarea name="" id="" cols="0" rows="7" class="contact__input">
          </textarea>
        </div>

        <div>
          <a href="#" class="button button--flex">
            Отправить Сообщение
            <i class="uil uil-message button__icon"></i>
          </a>
        </div>
      </form>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      contacts: [
        {
          title: "Позвоните Мне",
          subtitle: "8-983-580-39-82",
          iconClass: "uil-phone",
        },
        {
          title: "Email",
          subtitle: "iltw_life@mail.ru",
          iconClass: "uil-envelope",
        },
        {
          title: "Геопозиция",
          subtitle: "Россия - Горно-Алтайск",
          iconClass: "uil-map-marker",
        },
      ],
    };
  },
};
</script>

<style scoped>
.contact__container {
  row-gap: 3rem;
}

.contact__information {
  display: flex;
  margin-bottom: var(--mb-2);
}

.contact__icon {
  font-size: 2rem;
  color: var(--first-color);
  margin-right: var(--mb-0-75);
}

.contact__title {
  font-size: var(--h3-font-size);
  font-weight: var(--font-medium);
}

.contact__subtitle {
  font-size: var(--small-font-size);
  color: var(--text-color-light);
}

.contact__content {
  background-color: var(--input-color);
  border-radius: 0.5rem;
  padding: 0.75rem 1rem 0.25rem;
}

.contact__label {
  font-size: var(--small-font-size);
  color: var(--title-color);
}

.contact__input {
  width: 100%;
  background-color: var(--input-color);
  color: var(--text-color);
  font-family: var(--body-font);
  font-size: var(--normal-font-size);
  border: none;
  outline: none;
  padding: 0.25rem 0.5rem 0.5rem 0;
}

@media screen and (min-width: 568px) {
  .contact__container {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media screen and (min-width: 1024px) {
  .contact__form {
    width: 460px;
  }

  .contact__inputs {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
