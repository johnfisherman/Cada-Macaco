<template>
  <section class="contacto running-text-section">
    <h4>
      Tens algum provérbio a sugerir? Elogios a fazer? Encontraste a combinação
      perfeita, pronta a entrar nos cânones da Sabedoria Popular Portuguesa?
    </h4>
    <h4>Envia-nos uma mensagem!</h4>
    <form action="https://formspree.io/f/mgebaala" method="POST">
      <label>
        <span>Morada de email</span>
        <input required type="email" name="email" />
      </label>
      <label>
        <span>A tua mensagem</span>
        <textarea name="message" required rows="15"></textarea>
      </label>
      <!-- your other form fields go here -->
      <button class="button" type="submit">Enviar</button>
    </form>
  </section>
  <footer>
    <p>
      Uma experiência linguística de
      <a href="https://fredrocha.net">Fred Rocha</a> com a inspiração de
      <a href="https://madalenamarques.com" target="_blank">Madalena Marques</a
      >.
      <a href="https://github.com/johnfisherman/Cada-Macaco" target="_blank"
        >Código aberto</a
      >
      aberto a remixes e novas línguas.
    </p>
    <p>
      Logo e ícone por
      <a
        href="https://www.flaticon.com/authors/freepik"
        title="muted monkey"
        target="_blank"
        >Freepik</a
      >.
    </p>
    <p class="social-links">
      <a class="fr-icon" href="https://fredrocha.net" target="_blank">
        <img src="fr-logo-s.png" alt="Logo for fredrocha.net" />
      </a>
      <a
        class="mastodon-icon"
        href="https://mastodon.social/@john_fisherman"
        target="_blank"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="40"
          height="40"
          viewBox="0 0 2400 2400"
        >
          <path
            d="M288 128C129 128 0 257 0 416v960c0 159 129 288 288 288h960c159 0 288-129 288-288V416c0-159-129-288-288-288H288zm478.38 219.105h3.45c140.347 1.148 275.434 16.34 354.104 52.473 0 0 156.027 69.805 156.027 307.95 0 0 1.957 175.702-21.76 297.69-15.053 77.44-134.816 162.191-272.367 178.616-71.725 8.558-142.346 16.423-217.65 12.969-123.152-5.642-220.329-29.395-220.329-29.395 0 11.989.739 23.404 2.217 34.08 16.01 121.539 120.515 128.819 219.508 132.213 99.915 3.418 188.88-24.633 188.88-24.633l4.106 90.327s-69.885 37.53-194.382 44.431c-68.65 3.774-153.892-1.726-253.174-28.006-215.325-56.993-252.197-286.524-258.022-519.412-1.728-69.147-.665-134.348-.662-188.88.01-238.144 156.033-307.95 156.033-307.95 78.674-36.133 213.675-51.326 354.022-52.473zM607.544 533.18c-50.528 0-91.234 17.76-122.314 52.408-30.14 34.649-45.145 81.48-45.145 140.412v288.354h114.238V734.476c0-59 24.824-88.944 74.477-88.944 54.9 0 82.42 35.524 82.42 105.766V904.49h113.566V751.3c0-70.242 27.516-105.764 82.414-105.764 49.652 0 74.477 29.945 74.477 88.944v279.876h114.238V726.003c0-58.933-14.473-106.234-45.139-140.412-31.086-34.648-71.792-52.408-122.314-52.408-58.466 0-102.735 22.468-132 67.414L768 648.295l-28.455-47.7c-29.271-44.946-73.542-67.415-132.002-67.415z"
          />
        </svg>
      </a>
      <a
        class="github-icon"
        href="https://github.com/johnfisherman/Cada-Macaco"
        target="_blank"
      >
        <svg viewBox="0 0 1024 1024" xmlns="http://www.w3.org/2000/svg">
          <path
            d="m1024 525c0 225.9-146.6 417.9-348.8 485.8-25.6 5.1-35.2-10.9-35.2-24.4 0-17.2.6-72.3.6-140.8 0-48-16-78.7-34.5-94.7 113.9-12.8 233.6-56.3 233.6-252.8 0-56.3-19.9-101.7-52.5-137.6 5.1-12.8 23-65.3-5.1-135.7 0 0-42.9-14-140.8 52.5-41-11.5-84.5-17.3-128-17.3s-87.1 5.8-128 17.3c-97.9-65.9-140.8-52.5-140.8-52.5-28.2 70.4-10.3 122.9-5.1 135.7-32.7 35.9-52.5 81.9-52.5 137.6 0 195.9 119 240 232.9 252.8-14.7 12.8-28.1 35.2-32.6 68.5-29.4 13.4-103 35.2-149.1-42.2-9.6-15.4-38.4-53.2-78.7-52.5-42.9.6-17.3 24.3.6 33.9 21.8 12.2 46.7 57.6 52.5 72.3 10.2 28.8 43.5 83.9 172.1 60.2 0 42.9.7 83.2.7 95.3 0 13.5-9.6 28.8-35.2 24.4-203.5-67.9-350.1-259.2-350.1-485.8 0-282.9 229.1-512 512-512s512 229.1 512 512z"
            fill="#fff"
            fill-rule="evenodd"
          />
        </svg>
      </a>
    </p>
  </footer>
</template>
<style scoped>
.contacto {
  text-align: left;
}
form {
  display: flex;
  flex-direction: column;
  font-family: var(--ui-font-family);
  font-size: 0.9em;
}
form label {
  font-size: 0.9em;
}
form label span {
  width: 100%;
  display: flex;
  flex-direction: column;
  padding-bottom: 10px;
  font-weight: bold;
  /* border: 3px solid hotpink !important; */
}
form input,
form textarea {
  padding: 10px;
  font-family: var(--ui-font-family);
  font-size: 1em;
}

form input {
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.125);
  min-width: 350px;
  margin-bottom: 20px;
}
form textarea {
  margin-bottom: 20px;
  width: 90%;
}
form button {
  max-width: 220px;
  background-color: var(--accent-color);
  border: none;
  border: 1px solid #4e4e4e;
  width: 150px;
  margin: 0px 0px;
  padding-top: 10px;
  padding-bottom: 10px;
  font-size: 0.7em;
  border-radius: 4px;
  font-weight: bold;
}
form button:hover {
  transform: scale(1.1);
  cursor: pointer;
  transition: all ease-in-out 0.1s;
}
form button:active {
  transform: scale(1);
  cursor: pointer;
  background-color: aquamarine;
}
@media only screen and (min-width: 800px) {
  form textarea {
    width: 600px;
  }
}
a {
  color: #554994;
}
footer {
  font-size: 0.7em;
  padding: 20px 40px;
  background-color: var(--tertiary-color);
}
footer a:hover {
  font-style: italic;
}
</style>
