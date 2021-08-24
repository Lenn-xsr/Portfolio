<template>
  <aside>aside</aside>
</template>

<script>
export default {
  name: "Aside",
};
</script>

<style scoped>
aside {
  width: clamp(80px, 300px, 15vw);
  border-left: 1px solid var(--fading);
}
@media screen and (max-width: 1015px) {
  aside {
    width: 100%;
    height: max-content;
    padding: 1rem;
    border: none;
    border-top: 1px solid var(--fading);
  }
}
</style>