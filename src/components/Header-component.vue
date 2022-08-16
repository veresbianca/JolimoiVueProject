<template>
  <header>
    <div class="header-text__content">
      <span class="header-text__content--format">This is a page for beauty product search</span>
    </div>
    <BannerComponent />
  </header>
</template>

<script>
import BannerComponent from './Banner-component.vue'

export default {
  name: 'Header',
  components: {
    BannerComponent
  }
}
</script>

<style lang="css" scoped>
  :root {
    --header-background: #55D7FF;
  }


  header {
    grid-column: 1 / span 2;
    display: grid;
    grid-template-rows: 50% 50%;
  }

  .header-text__content {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    font-size: 1em;
    font-weight: bold;
    background-color: var(--header-background);
  }

  .header-text__content .header-text__content--format {
    max-width: 180px;
    text-align: center;
  }

  @media (min-width: 768px) {
    header {
      grid-template-columns: 1fr 1fr;
      grid-template-rows: auto;
    }


    .header-text__content {
      font-size: 1.5em;
    }

    .header-text__content .header-text__content--format {
      max-width: 280px;
    }
  }
</style>