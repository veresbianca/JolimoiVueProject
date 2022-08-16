<template>
  <div id="app">
    <HeaderComponent />
    <section class="body__container">
      <SearchComponent/>
    </section>
  </div>
</template>

<script>
import HeaderComponent from './components/Header-component.vue'
import SearchComponent from './components/Search-component.vue'

export default {
  name: 'app',
  components: {
    HeaderComponent,
    SearchComponent
  }
}
</script>

<style lang="css">

:root {
  --body-background: #DB0992;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.body__container {
  grid-column: 1 / span 2;
  padding: 3.8%;
  background-color: var(--body-background);
}

#app {
  display: grid;
  grid-template-rows: 2fr 1fr;
  grid-template-columns: 0;
  height: 100vh;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

@media (min-width: 768px) {
  .body__container {
    grid-column: 1 / span 2;
  }

  #app {
    grid-template-rows: 1fr 1fr;
  }
}

@media (min-width: 1025px) {
  .body__container {
    padding: 34px;
  }
}
</style>
