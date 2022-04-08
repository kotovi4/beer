<template>
  <h1>Randomaizer Beer</h1>
  <AppCard />
</template>

<script>
import AppCard from './components/app-card/AppCard.vue'


export default {
  name: 'App',
  components: {
    AppCard
  }
}
</script>

<style>
@import "~@/styles/fonts.css";

#app {
  font-family: "PT Root UI", Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin: 7% 0 60px 0;
}

html {
  background-color: var(--smoke);
}

h1 {
  font-size: 44px;
  line-height: 130%;
  margin-bottom: 60px;
}
</style>
