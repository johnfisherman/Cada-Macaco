<template>
  <nav>
    <router-link to="/">Cada Macaco</router-link> |
    <router-link to="/about">Contacto</router-link> |
    <router-link to="/como-assim">Como Assim?</router-link>
  </nav>
  <router-view />
</template>

<style>
@import "assets/styles/variables.css";

@font-face {
  font-family: "Castoro";
  src: local("Castoro"),
    url("../public/fonts/Castoro-Regular.ttf") format("truetype");
}

@font-face {
  font-family: "Alegreya SC";
  src: local("Alegreya SC"),
    url("../public/fonts/AlegreyaSC-Regular.ttf") format("truetype");
}

#app {
  font-family: var(--ui-font-family);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  font-size: var(--global-font-size);
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
}

nav a.router-link-exact-active {
  color: var(--active-link-color);
}
</style>
