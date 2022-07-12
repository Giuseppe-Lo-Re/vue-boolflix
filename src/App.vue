<template>
  <div id="app">

    <HeaderPage @runSearch="SearchText"/>
    
    <MainPage :searchtext="activeSearch"/>

  </div>
</template>

<script>
import HeaderPage from "./components/HeaderPage";
import  MainPage  from "./components/MainPage";

export default {
  name: 'App',
  components: {
    HeaderPage,
    MainPage
  
  },
  data() {
    return {
      activeSearch:''
    }
  },
  methods: {
    SearchText(userChoice) {
      this.activeSearch = userChoice;
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
