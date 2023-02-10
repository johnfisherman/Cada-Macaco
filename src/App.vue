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
      <router-link to="/como-assim">Como Assim?</router-link>
      <router-link to="/contacto">Contacto</router-link>
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
  font-family: "Avenir LT Std";
  src: local("Avenir LT Std"),
    url("../public/fonts/AvenirLTStd-Black.otf") format("opentype");
  src: local("Avenir-LT-Std"),
    url("../public/fonts/AvenirLTStd-Black.otf") format("opentype");
  font-style: normal;
  font-weight: 950;
}

@font-face {
  font-family: "Avenir LT Std";
  src: local("Avenir LT Std"),
    url("../public/fonts/AvenirLTStd-Medium.otf") format("opentype");
  src: local("Avenir-LT-Std"),
    url("../public/fonts/AvenirLTStd-Medium.otf") format("opentype");
  font-style: normal;
  font-weight: 400;
}

/* @font-face {
  font-family: "Avenir";
  src: local("Avenir"),
    url("../public/fonts/AvenirLTStd-Roman.otf") format("opentype");
  font-style: normal;
  font-weight: 550;
} */

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
  text-decoration: underline;
}

nav .logo {
}

nav .logo img {
  width: 50px;
}

nav .logo img:hover {
  transform: scale(1.1);
}

nav .navigation-items {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 0 0 0;
}
nav .navigation-items a {
  min-width: 120px;
  font-size: 16px;
  text-align: left;
  padding: 0 20px;
  color: var(--brand-color);
}
@media only screen and (min-width: 600px) {
  nav .navigation-items a {
    min-width: 200px;
    font-size: 18px;
  }
}
nav .navigation-items a:first-child {
  text-align: right;
}
.running-text-section {
  max-width: 900px;
  margin-bottom: 40px;
  padding: 20px;
  text-align: left;
  font-family: var(--ui-font-family);
  color: var(--main-font-color);
  text-align: left;
  font-size: 0.9em;
}
.running-text-section h1,
.running-text-section h2,
.running-text-section h3,
.running-text-section h4 {
  color: var(--main-font-color);
  font-weight: 950;
}
@media only screen and (min-width: 800px) {
  .running-text-section {
    padding: 20px 40px;
  }
}
footer .social-links svg:hover {
  transform: scale(1.1);
  transition: all ease-in-out 0.1s;
}
footer .social-links .mastodon-icon path {
  fill: slateblue;
}
footer .social-links .github-icon path {
  fill: black;
}
footer .social-links .github-icon svg {
  width: 28px;
  height: 28px;
  padding-bottom: 11px;
}
footer .social-links .mastodon-icon svg {
  width: 40px;
  height: 40px;
}
</style>
