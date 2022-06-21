<template>
  <header class="header" id="header">
    <nav class="nav container">
      <a href="#" class="nav__logo">Никита</a>

      <div class="nav__menu" :class="{ showMenu: !isHidden }">
        <ul class="nav__list grid">
          <li v-for="link in links" :key="link.name" class="nav__item">
            <a
              @click="isHidden = true"
              :href="'#' + link.sectionId"
              class="nav__link"
            >
              <i class="uil nav__icon" :class="link.iconClass"> </i>
              {{ link.name }}
            </a>
          </li>
        </ul>

        <i @click="isHidden = true" class="uil uil-times nav__close"></i>
      </div>

      <div class="nav__btns">
        <i @click="changeTheme" class="uil change-theme" id="theme-button"></i>

        <div @click="isHidden = false" class="nav__toggle">
          <i class="uil uil-apps"></i>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  mounted() {
    this.selectedTheme = localStorage.getItem("selected-theme");
    this.selectedIconTheme = localStorage.getItem("selected-icon");

    if (!this.selectedTheme || !this.selectedIconTheme) {
      this.selectedTheme = "dark";
      this.selectedIconTheme = this.darkIconTheme;
    }

    document.body.classList[this.selectedTheme === "dark" ? "add" : "remove"](
      this.darkTheme
    );

    document
      .getElementById("theme-button")
      .classList.add(this.selectedIconTheme);

    window.addEventListener("scroll", this.handleScroll);
  },

  unmounted() {
    window.removeEventListener("scroll", this.handleScroll);
  },

  data() {
    return {
      selectedTheme: "",
      selectedIconTheme: "",

      darkTheme: "dark-theme",

      darkIconTheme: "uil-sun",
      lightIconTheme: "uil-moon",

      links: [
        { name: "Домой", sectionId: "home", iconClass: "uil-estate" },
        { name: "Обо Мне", sectionId: "about", iconClass: "uil-user" },
        { name: "Навыки", sectionId: "skills", iconClass: "uil-file-alt" },
        {
          name: "Услуги",
          sectionId: "services",
          iconClass: "uil-briefcase-alt",
        },
        { name: "Портфолио", sectionId: "portfolio", iconClass: "uil-scenery" },
        {
          name: "Контакты",
          sectionId: "contact",
          iconClass: "uil-message",
        },
      ],
      isHidden: true,
    };
  },

  methods: {
    handleScroll() {
      const scrollY = window.scrollY;

      this.links.forEach((link) => {
        const section = document.getElementById(link.sectionId);
        const sectionHeight = section.offsetHeight;
        const sectionTop = section.offsetTop - 50;

        const htmlLink = document.querySelector(
          ".nav__menu a[href*=" + link.sectionId + "]"
        );

        if (scrollY > sectionTop && scrollY <= sectionTop + sectionHeight) {
          htmlLink.classList.add("active-link");
        } else {
          htmlLink.classList.remove("active-link");
        }
      });

      const nav = document.getElementById("header");
      if (scrollY >= 80) nav.classList.add("scroll-header");
      else nav.classList.remove("scroll-header");
    },

    getCurrentTheme() {
      return document.body.classList.contains(this.darkTheme)
        ? "dark"
        : "light";
    },

    changeTheme() {
      document.body.classList.toggle(this.darkTheme);

      const themeButton = document.getElementById("theme-button");
      if (this.selectedTheme === "dark") {
        themeButton.classList.remove(this.darkIconTheme);
        this.selectedTheme = "light";
        this.selectedIconTheme = this.lightIconTheme;
      } else {
        themeButton.classList.remove(this.lightIconTheme);
        this.selectedTheme = "dark";
        this.selectedIconTheme = this.darkIconTheme;
      }
      themeButton.classList.add(this.selectedIconTheme);

      localStorage.setItem("selected-theme", this.selectedTheme);
      localStorage.setItem("selected-icon", this.selectedIconTheme);
    },
  },
};
</script>

<style scoped>
.header {
  width: 100%;
  position: fixed;
  bottom: 0;
  left: 0;
  z-index: var(--z-fixed);
  background-color: var(--body-color);
}

.nav {
  max-width: 968px;
  height: var(--header-height);
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav__logo,
.nav__toggle {
  color: var(--title-color);
  font-weight: var(--font-medium);
}

.nav__logo:hover {
  color: var(--first-color);
}

.nav__toggle {
  font-size: 1.1rem;
  cursor: pointer;
}

.nav__toggle:hover {
  color: var(--first-color);
}

@media screen and (max-width: 767px) {
  .nav__menu {
    position: fixed;
    bottom: -100%;
    left: 0;
    width: 100%;
    background-color: var(--body-color);
    padding: 2rem 1.5rem 4rem;
    box-shadow: 0 -1px 4px rgba(0, 0, 0, 0.15);
    border-radius: 1.5rem 1.5rem 0 0;
    transition: 0.3s;
  }
}

.nav__list {
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.nav__link {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-size: var(--small-font-size);
  color: var(--title-color);
  font-weight: var(--font-medium);
}

.nav__link:hover {
  color: var(--first-color);
}

.nav__icon {
  font-size: 1.2rem;
}

.nav__close {
  position: absolute;
  right: 1.3rem;
  bottom: 0.5rem;
  font-size: 1.5rem;
  cursor: pointer;
  color: var(--first-color);
}

.nav__close:hover {
  color: var(--first-color-alt);
}

.showMenu {
  bottom: 0;
}

.active-link {
  color: var(--first-color);
}

.scroll-header {
  box-shadow: 0 -1px 4px rgba(0, 0, 0, 0.5);
}

.nav__btns {
  display: flex;
  align-items: center;
}

.change-theme {
  font-size: 1.25rem;
  color: var(--title-color);
  margin-right: var(--mb-1);
  cursor: pointer;
}

.change-theme:hover {
  color: var(--first-color);
}

@media screen and (max-width: 350px) {
  .nav__menu {
    padding: 2rem 0.25rem 4rem;
  }

  .nav__list {
    column-gap: 0;
  }
}

@media screen and (min-width: 768px) {
  .header {
    top: 0;
    bottom: initial;
    padding: 0 1rem;
  }

  .nav {
    height: calc(var(--header-height) + 1.5rem);
    column-gap: 1rem;
  }

  .nav__icon,
  .nav__close,
  .nav__toggle {
    display: none;
  }

  .nav__list {
    display: flex;
    column-gap: 2rem;
  }

  .nav__menu {
    margin-left: auto;
  }

  .change-theme {
    margin: 0;
  }
}

@media screen and (min-width: 1024px) {
  .header {
    padding: 0;
  }
}
</style>
