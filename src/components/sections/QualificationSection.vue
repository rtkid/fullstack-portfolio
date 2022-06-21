<template>
  <section class="qualification section">
    <h2 class="section__title">Квалификация</h2>
    <span class="section__subtitle">Мой путь</span>

    <div class="qualification__container container">
      <div class="qualification__tabs">
        <div
          @click="showQualification(0)"
          class="qualification__button button--flex"
          :class="{ qualifications__active: qualifications[0].active }"
        >
          <i class="uil uil-graduation-cap qualification__icon"></i>
          Образование
        </div>

        <div
          @click="showQualification(1)"
          class="qualification__button button--flex"
          :class="{ qualifications__active: qualifications[1].active }"
        >
          <i class="uil uil-briefcase-alt qualification__icon"></i>
          Работа
        </div>
      </div>

      <div class="qualification__sections">
        <div
          v-for="qua in qualifications"
          :key="qua.id"
          v-show="qua.active === true"
          class="qualification__content"
        >
          <div
            v-for="point in qua.points"
            :key="point.name"
            class="qualification__data"
          >
            <div v-if="point.id % 2 === 0"></div>

            <div v-if="point.id % 2 === 0">
              <span class="qualification__rounder"></span>
              <span
                v-if="qua.points.length !== point.id"
                class="qualification__line"
              ></span>
            </div>

            <div>
              <h3 class="qualification__title">{{ point.name }}</h3>
              <span class="qualification__subtitle">{{ point.city }}</span>
              <div class="qualification__calendar">
                <i class="uil uil-calendar-alt"></i>
                {{ point.years }}
              </div>
            </div>

            <div v-if="point.id % 2 === 1">
              <span class="qualification__rounder"></span>
              <span
                v-if="qua.points.length !== point.id"
                class="qualification__line"
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
      qualifications: [
        {
          id: 0,
          active: true,
          points: [
            {
              id: 1,
              name: "Computer Enginner",
              city: "Youtube",
              years: "2019-2022",
            },
            {
              id: 2,
              name: "Web Developer",
              city: "Youtube",
              years: "2021-2022",
            },
          ],
        },
        {
          id: 1,
          active: false,
          points: [
            {
              id: 1,
              name: "В поиске",
              city: "",
              years: "2022",
            },
          ],
        },
      ],
    };
  },

  methods: {
    showQualification(idx) {
      this.qualifications[idx].active = true;
      const idxOther = idx ? 0 : 1;

      this.qualifications[idxOther].active = false;
    },
  },
};
</script>

<style scoped>
.qualification__tabs {
  display: flex;
  justify-content: space-evenly;
  margin-bottom: var(--mb-2);
}

.qualification__button {
  font-size: var(--h3-font-size);
  font-weight: var(--font-medium);
  cursor: pointer;
}

.qualification__button:hover {
  color: var(--first-color);
}

.qualification__icon {
  font-size: 1.8rem;
  margin-right: var(--mb-0-25);
}

.qualification__data {
  display: grid;
  grid-template-columns: 1fr max-content 1fr;
  column-gap: 1.5rem;
}

.qualification__title {
  font-size: var(--normal-font-size);
  font-weight: var(--font-medium);
}

.qualification__subtitle {
  display: inline-block;
  font-size: var(--small-font-size);
  margin-bottom: var(--mb-1);
}

.qualification__calendar {
  font-size: var(--smaller-font-size);
  color: var(--text-color-light);
}

.qualification__rounder {
  display: inline-block;
  width: 13px;
  height: 13px;
  background-color: var(--first-color);
  border-radius: 50%;
}

.qualification__line {
  display: block;
  width: 1px;
  height: 100%;
  background-color: var(--first-color);
  transform: translate(6px, -7px);
}

.qualifications__active {
  color: var(--first-color);
}

@media screen and (max-width: 350px) {
  .qualification__data {
    gap: 0.5rem;
  }
}

@media screen and (min-width: 568px) {
  .qualification__sections {
    display: grid;
    grid-template-columns: 0.6fr;
    justify-content: center;
  }
}

@media screen and (min-width: 768px) {
  .qualification__tabs {
    justify-content: center;
  }

  .qualification__button {
    margin: 0 var(--mb-1);
  }

  .qualification__sections {
    grid-template-columns: 0.5fr;
  }
}
</style>
