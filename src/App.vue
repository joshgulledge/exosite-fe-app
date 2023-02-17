<template>
  <Header/>
  <MainPage msg="Welcome to Your Insight Test Portal" />
</template>

<script>
import MainPage from "./components/MainPage.vue";
import Header from "./components/Header.vue";

export default {
  data () {
    return {
      name: "App",
    }
  },
 components: {
    MainPage,
    Header
  },
  computed: {
    
  },
  mounted() {
    
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
