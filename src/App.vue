<script lang="ts">
import HomeViewVue from './views/HomeView.vue'
</script>

<template>
  <div class="app-container">
    <header>
      <img src="./assets/logo.png" width="300" />
      <div class="icon-container">
        <font-awesome-icon icon="bell" class="fa-lg fa-black" />
        <font-awesome-icon icon="cog" class="fa-lg fa-black" />
        <font-awesome-icon icon="sign-out-alt" class="fa-lg fa-black" />
      </div>
    </header>
    <main>
      <RouterView />
    </main>
  </div>
</template>

<style scoped>
.app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

header {
  line-height: 1.5;
  max-height: 10vh;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  z-index: 1;
  background-color: white;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  padding-left: 10%;
  padding-right: 10%;
}

main {
  flex: 1;
  margin-top: 10vh;
}

/* Rest of the CSS styles */
.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-right: 10%;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav ul {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }

  .icon-container {
    display: flex;
    justify-content: space-between;
    width: 20%;
    padding-right: 200px;
  }

  .fa-lg {
    font-size: 2em;
  }

  .fa-black {
    color: black;
  }
}
</style>
