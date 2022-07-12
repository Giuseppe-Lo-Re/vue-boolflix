<template>
  <div id="app">

    <HeaderPage @runSearch="SearchText()"/>
    
    <MainPage />

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
      
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
