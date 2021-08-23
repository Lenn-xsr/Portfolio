<template>
  <div
    class="project-content"
    :style="{ animation: `project-from-bottom ${animationTime}s` }"
  >
    <h1>{{ project.title }}</h1>
    <div class="project-description">
      <div>
        <small>&lt;p></small>
        <hr />
        <small>&lt;/p></small>
      </div>
      <p>― {{ project.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Project",
  props: ["project", "animationTime"],
};
</script>

<style scoped>
.project-content {
  position: relative;
  width: 100%;
  border: 1px solid var(--secondary-fading);
  padding: 3.5rem 2rem;
  overflow: hidden;
  min-height: 351px;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  aspect-ratio: 10/9;
}

.project-content h1 {
  font-size: 1.5rem;
  margin-bottom: 5px;
  animation: slide-from-bottom 2.5s;
  width: max-content;
  position: relative;
  z-index: 1;
}

.project-content h1::before {
  content: "";
  background-color: var(--lighted-fading);
  height: 25%;
  width: max-content;
  border-radius: 1px;
  position: absolute;
  width: 100%;
  bottom: 0;
  animation: width-animation 2.3s;
  z-index: -1;
}

.project-description {
  display: flex;
}

.project-description div {
  display: flex;
  flex-direction: column;
  z-index: 1;
}

.project-description div hr {
  border-left: 1px dashed var(--fading);
  height: 100%;
  color: transparent;
  padding: 0;
  margin: 2px 7px;
  animation: dashed-anim 3s;
}

.project-description p {
  padding: 16px 0;
  margin: 10px 10px 10px -10px;
  color: var(--secondary-fading);
  animation: slide-from-left 3.2s;
}

.project-description small {
  color: var(--fading);
}

@keyframes slide-from-left {
  0% {
    opacity: 0;
    transform: translate3d(-15px, 0, 0);
  }
  50% {
    opacity: 0;
  }
  100% {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

@media screen and (min-width: 1824px) {
  .project-content {
    justify-content: center;
  }

  .project-content h1 {
    margin-bottom: 10px;
  }
}
</style>