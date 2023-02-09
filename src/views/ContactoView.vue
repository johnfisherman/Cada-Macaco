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
      <a
        href="https://github.com/johnfisherman/os-caes-ladram-no-seu-galho"
        target="_blank"
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
  width: 100%;
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
