<template>
  <header>

    <!-- Logo -->
    <div class="logo">
      <img src="../assets/img/logo.png" alt="logo">
    </div>

    <div class="form">

      <!-- Input -->
      <input 
        type="text" 
        name="search" 
        id="search"
        placeholder="Cosa vuoi guardare?"
        v-model="userSearch"
        @keyup.enter="$emit('runSearch', userSearch)"
      >

      <!-- Button -->
      <button 
        type="submit"
        @click="$emit('runSearch', userSearch)"
      >
        cerca
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

  img {
    width: 150px;
    padding-top: 7px;
    cursor: pointer;
  }

  input {
    padding: 10px;
  }
  
  button {
    margin-left: 10px;
    padding: 10px;
    background-color: red;
    color:white;
  }
}
</style>