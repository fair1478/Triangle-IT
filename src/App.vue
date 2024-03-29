<script setup>
import HelloWorld from "./components/HelloWorld.vue";
import InputForm from "./components/InputForm.vue";
</script>

<template>
  <header>
    <img
      alt="Vue logo"
      class="logo"
      src="./assets/logo.svg"
      width="125"
      height="125"
    />

    <div class="wrapper">
      <HelloWorld msg="Simple Triangle program" />
    </div>
  </header>

  <main>
    <InputForm />
  </main>

  <footer>
    <p>Assignment in IT Entrepreneurship And Management 2566</p>
    <p>
      Made with ❤️ by
      <a href="https://github.com/fair1478/Triangle-IT"
        >64011100, 64011225, 64011308</a
      >
    </p>
  </footer>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

footer {
  margin-top: 2rem;
  text-align: center;
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
}
</style>
