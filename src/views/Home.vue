<template>
  <main>
    <Header />
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
import Header from "@/components/Basics/Header.vue";
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
  components: { Header, Project },
};
</script>

<style scoped>
main {
  display: flex;
}

.projects-content {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  overflow: hidden;
}

.project-wrapper {
  display: grid;
  place-content: center;
}

.projects-content .project-wrapper:not(:last-child) {
  border-right: 1px solid var(--fading);
  margin-right: -2px;
}
</style>