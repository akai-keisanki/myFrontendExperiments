<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </nav>
  </header>

  <RouterView />
</template>

<style scoped lang="scss">
header {
  max-height: 100vh;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-content: flex-start;
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  background-color: $bg-1;
  width: 100vw;
}

.logo {
  width: 32px;
}

nav {
  width: 100%;
  text-align: center;
  display: flex;
  flex-direction: row;
  align-content: flex-start;
  justify-content: flex-start;
}

nav a {
  padding: 2em;
}
</style>
