<template>
  <main>
    <Sidebar />
    <article class="projects-content">
      <section
        class="project-wrapper"
        v-for="(project, index) in projects"
        :key="project.title"
      >
        <Project
          :project="project"
          :animation-time="
            (index > 1 ? index / index : index <= 0 ? index : index - 0.5) + 0.5
          "
        />
      </section>
    </article>
  </main>
</template>

<script>
import Sidebar from "@/components/Basics/Sidebar.vue";
import Project from "@/components/Project.vue";
import { projects } from "@/test.json";

export default {
  name: "Home",
  data() {
    return {
      projects,
      test: 0.5,
    };
  },
  components: { Sidebar, Project },
};
</script>

<style scoped>
main {
  display: flex;
}

.projects-content {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}

.project-wrapper {
  display: grid;
  place-content: center;
}

.projects-content .project-wrapper:not(:last-child) {
  border-right: 1px solid var(--fading);
  margin-right: -2px;
}

/* .projects-content .project-content:nth-child(1) {
  animation: project-from-bottom 0.5s;
}

.projects-content .project-content:nth-child(2) {
  animation: project-from-bottom 1s;
}

.projects-content .project-content:nth-child(3) {
  animation: project-from-bottom 1.5s;
} */
</style>