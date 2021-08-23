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
  padding: 3.5rem 2rem;
  width: clamp(100px, 300px, 15vw);
  border-left: 1px solid var(--fading);
}
</style>