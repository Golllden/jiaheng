<template>
  <div id="app">
    <!-- <nav>
      <router-link to="/">試算</router-link> |
      <router-link to="/UpdatePrice"> Revise </router-link>
    </nav> -->
    <router-view />
  </div>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  border: 0;
  outline: 0;
  font-weight: inherit;
  font-style: inherit;
  font-size: 100%;
  font-family: inherit;
  vertical-align: baseline;
}

body {
  overflow-x: hidden;
}

nav {
  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #9e7d56;
    }
  }
}
</style>
