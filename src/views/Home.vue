<template>
  <main>
    <Header :setPage="setPage" :pagesTotal="pagesTotal" />
    <article class="projects-content">
      <section
        class="project-wrapper"
        v-for="(project, index) in getPageProjects"
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
  components: { Header, Project },
  data() {
    return {
      projects,
      perPage: 3,
      currentPage: 0,
    };
  },
  computed: {
    getPageProjects() {
      const newList = [...this.projects];
      const offset =
        this.currentPage > 0
          ? this.perPage * this.currentPage
          : this.currentPage;
      const range =
        this.currentPage > 0
          ? this.perPage * (this.currentPage + 1)
          : this.perPage;

      return [...newList.slice(offset, range)];
    },
    pagesTotal() {
      const total = this.projects.length / this.perPage;
      return total !== Infinity ? Math.ceil(total) : 0;
    },
  },
  methods: {
    setPage(page) {
      this.currentPage = page - 1;
    },
  },
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