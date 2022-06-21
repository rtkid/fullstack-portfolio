<template>
  <section class="skills section" id="skills">
    <h2 class="section__title">Навыки</h2>
    <span class="section__subtitle">Мой технический уровень</span>

    <div class="skills__container container grid">
      <div
        v-for="side in developmentSide"
        :key="side.name"
        class="skills__content"
        :class="{
          skills__open: side.show,
          skills__close: !side.show,
        }"
      >
        <div @click="open(side)" class="skills__header">
          <i class="uil skills__icon" :class="side.iconClass"></i>

          <div>
            <h1 class="skills__title">{{ side.name }}</h1>
            <span class="skills__subtitle"> Больче чем {{ side.age }} год</span>
          </div>

          <i class="uil uil-angle-down skills__arrow"></i>
        </div>

        <div class="skills__list grid">
          <div
            v-for="skill in side.skills"
            :key="skill.name"
            class="skills__data"
          >
            <div class="skills__titles">
              <h3 class="skills__name">{{ skill.name }}</h3>
              <span class="skills__number">{{ skill.percent }}</span>
            </div>

            <div class="skills__bar">
              <span
                class="skills__percentage"
                :style="'width: ' + skill.percent"
              ></span>
            </div>
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
      developmentSide: [
        {
          show: true,
          name: "Fronted developer",
          age: "1",
          iconClass: "uil-brackets-curly",
          skills: [
            { name: "HTML", percent: "90%" },
            { name: "CSS", percent: "80%" },
            { name: "JavaScript", percent: "75%" },
            { name: "Vue", percent: "85%" },
          ],
        },
        {
          show: false,
          name: "Backend developer",
          age: "1",
          iconClass: "uil-server-network",
          skills: [
            { name: "JavaScript", percent: "75%" },
            { name: "NodeJS", percent: "70%" },
            { name: "Express", percent: "75%" },
            { name: "MongoDB", percent: "80%" },
          ],
        },
        {
          show: false,
          name: "Designer",
          age: "1",
          iconClass: "uil-swatchbook",
          skills: [
            { name: "Figma", percent: "90%" },
            { name: "Sketch", percent: "85%" },
            { name: "Photoshop", percent: "75%" },
          ],
        },
      ],
    };
  },

  methods: {
    open(side) {
      side.show = !side.show;

      if (side.show) {
        this.developmentSide.forEach((element) => {
          if (side.name != element.name) {
            element.show = false;
          }
        });
      }
    },
  },
};
</script>

<style scoped>
.skills__container {
  row-gap: 0;
}

.skills__content {
  transition: 0.3s;
}

.skills__header {
  display: flex;
  align-items: center;
  margin-bottom: var(--mb-2-5);
  cursor: pointer;
}

.skills__icon,
.skills__arrow {
  font-size: 2rem;
  color: var(--first-color);
}

.skills__icon {
  margin-right: var(--mb-0-75);
}

.skills__title {
  font-size: var(--h3-font-size);
}

.skills__subtitle {
  font-size: var(--small-font-size);
  color: var(--text-color-light);
}

.skills__arrow {
  margin-left: auto;
  transition: 0.4s;
}

.skills__list {
  row-gap: 1.5rem;
  padding-left: 2.7rem;
}

.skills__titles {
  display: flex;
  justify-content: space-between;
  margin-bottom: var(--mb-0-5);
}

.skills__name {
  font-size: var(--normal-font-size);
  font-weight: var(--font-medium);
}

.skills__bar,
.skills__percentage {
  height: 5px;
  border-radius: 0.25rem;
}

.skills__bar {
  background-color: var(--first-color-lighter);
}

.skills__percentage {
  display: block;
  background-color: var(--first-color);
}

.skills__open .skills__list {
  height: max-content;
  margin-bottom: var(--mb-2-5);
}

.skills__open .skills__arrow {
  transform: rotate(-180deg);
}

.skills__close .skills__list {
  height: 0;
  overflow: hidden;
}

@media screen and (max-width: 350px) {
  .skills__title {
    font-size: var(--normal-font-size);
  }
}

@media screen and (min-width: 568px) {
  .skills__container {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
