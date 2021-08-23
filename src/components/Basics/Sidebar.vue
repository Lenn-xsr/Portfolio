<template>
  <nav>
    <h1><small>&lt; </small> Lennart <small> /></small></h1>
  </nav>
</template>

<script>
export default {
  name: "Sidebar",
};
</script>

<style scoped>
nav {
  padding: 3.5rem 2rem;
  width: clamp(100px, 250px, 10vw);
  min-width: max-content;
  height: 100vh;
  border-right: 1px solid var(--fading);
}

h1 {
  font-size: 1.3rem;
  text-align: center;
  animation: slide-from-left 1s;
}

h1 small {
  font-size: 1rem;
}
</style>