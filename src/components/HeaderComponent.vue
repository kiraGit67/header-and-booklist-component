<template>
  <header class="header">
    <section class="header__section">
      <p class="header__task-name">{{ headerEmoticons }} {{ headerTitle }}</p>
      <div class="header__bootcamp-info-wrapper">
        <nav class="header__nav">
          <a href="#" class="header__nav-item header__nav-item--active">Home</a
          >&nbsp;&nbsp;
          <base-button
            :text="baseButtonText"
            variant="secondary"
            :style="baseButtonStyle"
          />
        </nav>
        <a :href="headerLink" class="header__bootcamp-link">{{
          headerLinkText
        }}</a>
      </div>
    </section>
  </header>
</template>

<script>
import BaseButton from "@/components/BaseButton.vue";

export default {
  data() {
    return {
      headerTitle: "CodingBootcamp Europe BookStore",
      headerEmoticons: "📚 👀 📖 ",
      headerLink: "https://www.coding-bootcamps.eu/",
      headerLinkText: "coding-bootcamps.eu",
      baseButtonStyle: "font-size: 1.1rem",
      baseButtonText: "Book Store",
    };
  },
  components: {
    BaseButton,
  },
};
</script>

<style scoped>
.header {
  background-color: var(--primary);
  color: #fff;
  margin-bottom: 20px;
}

.header__task-name {
  font-size: 1.4rem;
  margin: 0;
}

.header__section {
  padding: 10px 10px;
}

.header__bootcamp-info-wrapper {
  font-size: 1rem;
  margin: 0;
}

.header__bootcamp-link {
  background-color: var(--primary);
  color: #fff;
  text-decoration: none;
  display: none;
  margin-left: 50px;
  padding: 0px 20px;
}

.header__nav {
  margin: 30px 0 10px 0px;
}

.header__nav-item {
  color: #fff;
  border-radius: 3px;
  display: inline;
  padding: 10px 10px;
}

.header__nav-item--active {
  color: #fff;
  background-color: var(--primary-dark);
}

@media only screen and (min-width: 1140px) {
  .header {
    font-size: 1.5rem;
    margin-bottom: 50px;
  }

  .header__section {
    display: flex;
    padding: 0px 20px;
    line-height: 2.5;
  }

  .header__bootcamp-info-wrapper {
    margin-left: auto;
    display: flex;
    line-height: 3.4;
  }

  .header__task-name {
    width: 50%;
  }

  .header__bootcamp-link {
    display: block;
  }

  .header__nav {
    margin: 0px;
  }
}
</style>
