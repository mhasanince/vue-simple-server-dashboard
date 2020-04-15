<template>
  <div id="app">
    <Header />
    <Content />
    <Footer />
  </div>
</template>

<script>
import Header from './components/shared/Header.vue';
import Content from './components/shared/Content.vue';
import Footer from './components/shared/Footer.vue';

export default {
  name: 'App',
  components: {
    Header,
    Content,
    Footer,
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #4d4d4d;
  margin: 0 10%;
}
</style>
