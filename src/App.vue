<template>
  <nav>
    <div class="logo">
      <router-link to="/"
        ><img
          src="macaco-small.png"
          alt="Logotipo do site - macaco com a boca tapada"
          title="Cada Macaco - Home"
      /></router-link>
    </div>
    <div class="navigation-items">
      <router-link to="/contacto">Contacto</router-link>
      <router-link to="/como-assim">Como Assim?</router-link>
    </div>
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

body {
  background-color: var(--quadri-color);
  padding: 0;
}

#app {
  font-family: var(--ui-font-family);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  font-size: var(--global-font-size);
}

a {
  color: var(--accent-color-strong);
}

nav {
  margin: 0 auto;
  background-color: var(--tertiary-color);
  display: flex;
  flex-direction: column;
  padding: 20px;
}

nav a {
  font-size: 18px;
  text-transform: uppercase;
  font-weight: bold;
  color: var(--main-font-color);
  text-decoration: none;
}

nav a:hover {
  text-decoration: underline;
}

nav a.router-link-exact-active {
  color: var(--active-link-color);
}

nav .logo {
  /* border: 1px solid hotpink !important; */
}

nav .logo img {
  /* border: 1px solid blue !important; */
  width: 50px;
}

nav .navigation-items {
  /* border: 3px solid yellow !important; */
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 0 0 0;
}
nav .navigation-items a {
  /* border: 3px solid red !important; */
  min-width: 200px;
  text-align: left;
  padding: 0 20px;
  color: var(--brand-color);
}
nav .navigation-items a:first-child {
  text-align: right;
}
.running-text-section {
  max-width: 900px;
  margin-bottom: 40px;
  padding: 20px 40px;
  text-align: left;
  font-family: var(--ui-font-family);
  text-align: left;
  margin-left: 40px;
  font-size: 0.9em;
}
</style>
