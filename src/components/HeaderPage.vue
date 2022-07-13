<template>
  <header>

    <!-- Logo -->
    <h1 class="logo">
      BOOFLIX
    </h1>
    <div class="form">

      <!-- Input -->
      <input 
        type="text" 
        name="search" 
        id="search"
        placeholder="Search"
        v-model="userSearch"
        @keyup.enter="$emit('runSearch', userSearch)"
      >

      <!-- Button -->
      <button 
        type="submit"
        @click="$emit('runSearch', userSearch)"
      >
        Search
      </button>
    </div>
  </header>
</template>

<script>
export default {
name: "HeaderPage",
data() {
  return {
    userSearch: ''
  }
}
}
</script>

<style lang="scss" scoped>
@import "../style/common.scss";

header {
  height: 70px;
  background-color: black;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-inline: 20px;

  .logo {
    color: red;
    font-size: 24px;
    text-align: left;
  }
}
</style>