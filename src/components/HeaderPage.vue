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
          placeholder="Search"
          v-model="userText"
        >

        <!-- Button -->
        <button 
          type="submit"
          @click="$emit('runSearch', userText)"
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
    text: ''
  }
}
}
</script>

<style lang="scss" scoped>
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

  .form {
    
    display: inline-block;
  }
}
</style>