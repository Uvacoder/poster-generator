<template>
  <main>
    <header>
      <div class="header-content">
        <img src="./assets/logo-uniform.png" width="196" alt="Uniform logo" />
      </div>
    </header>
    <generator />
  </main>
</template>

<script>
import generator from "./components/generator.vue";

export default {
  name: "App",
  components: {
    generator,
  },
};
</script>

<style>
body {
  margin: 0;
  font-family: system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial,
    sans-serif, Apple Color Emoji, Segoe UI Emoji;
  color: #1d3557;
}

header {
  height: 96px;
  background: rgb(9, 53, 87);
}

.header-content {
  max-width: 800px;
  margin: 0;
  padding: 0 32px;
}

header img {
  margin: 9px 0 0;
}
</style>
