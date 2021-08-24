<template>
  <header>
    <nav>
      <h1><small>&lt; </small> Lennart <small> /></small></h1>
      <ul class="side-menu">
        <li
          v-for="page in pagesTotal"
          :key="page"
          :class="currentPage == page ? 'menu-btn active' : 'menu-btn'"
          :style="{ 'animation-duration': `${page - 0.5}s` }"
          @click.prevent="setPage(page), (currentPage = page)"
        ></li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: ["pagesTotal", "setPage"],
  data() {
    return {
      currentPage: 1,
    };
  },
};
</script>

<style scoped>
header {
  padding: 3.5rem 2rem;
  width: clamp(100px, 250px, 10vw);
  min-width: max-content;
  height: 100vh;
  border-right: 1px solid var(--fading);
}

nav {
  height: 100%;
  display: grid;
}

h1 {
  font-size: 1.3rem;
  text-align: center;
  animation: slide-from-left 1s;
}

h1 small {
  font-size: 1.2rem;
}

.side-menu {
  align-self: baseline;
}

.side-menu .menu-btn:not(:first-child) {
  margin-top: 3px;
}

.menu-btn {
  display: grid;
  width: 30px;
  height: 10px;
  place-content: center;
  justify-content: flex-start;
  cursor: pointer;
  animation: menu-from-left;
}

.menu-btn::before {
  content: "";
  width: 15px;
  height: 3px;
  background-color: var(--fading);
  border-radius: 10px;
  transition: all 0.3s;
}

.menu-btn.active::before,
.menu-btn:hover::before {
  width: 20px;
  background-color: var(--secondary);
}

@media screen and (max-width: 1015px) {
  header {
    width: 100%;
    height: max-content;
    border: none;
    padding: 2.5rem 1rem;
    border-bottom: 1px solid var(--fading);
  }

  h1 {
    animation: slide-from-top 1s;
  }

  .side-menu {
    margin-top: 25px;
    justify-self: center;
    display: flex;
  }

  .menu-btn {
    transform: rotate(90deg);
    animation: slide-from-bottom-90deg;
  }

  .side-menu .menu-btn:not(:first-child) {
    margin-top: 0;
  }
}
</style>