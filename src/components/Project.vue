<template>
  <div
    class="project-content"
    :style="{ 'animation-duration': `${animationTime}s` }"
  >
    <h1>{{ project.title || project.name }}</h1>
    <div class="project-description">
      <div>
        <small>&lt;p></small>
        <hr />
        <small>&lt;/p></small>
      </div>
      <p>― {{ project.description || "No description given." }}</p>
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
  animation: project-from-bottom;
  aspect-ratio: 9/9;
}

.project-content h1 {
  font-size: 1.5rem;
  margin-bottom: 5px;
  animation: slide-from-bottom 2.5s;
  width: -moz-fit-content;
  width: fit-content;
  position: relative;
  text-transform: capitalize;
  z-index: 1;
}

.project-content h1::before {
  content: "";
  background-color: var(--lighted-fading);
  height: 6px;
  border-radius: 1px;
  position: absolute;
  width: calc(100% + 8px);
  bottom: 3px;
  left: -4px;
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
  user-select: none;
}

.project-description div hr {
  border: none;
  border-left: 1px dashed var(--fading);
  height: 100%;
  color: transparent;
  padding: 0;
  margin: 10px 0px;
  animation: dashed-anim 3s;
}

.project-description p {
  padding: 16px 0;
  margin: 10px 10px 10px -10px;
  animation: slide-from-left 3.2s;
}

.project-description small {
  color: var(--fading);
  font-size: 0.9rem;
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

@media screen and (max-width: 1443px) {
  .project-content h1 {
    font-size: 1rem;
  }
}

@media screen and (max-width: 1015px) {
  .project-content {
    max-width: 100vw;
  }
}
</style>