<template>
  <main>
    <Header :setPage="setPage" :pagesTotal="pagesTotal" />
    <article
      class="projects-content"
      :style="{ 'grid-template-columns': `repeat(${perPage}, 1fr)` }"
    >
      <section
        class="project-wrapper"
        v-for="(project, index) in getPageProjects"
        :key="project.title || project.id"
      >
        <Project
          :project="project"
          :animation-time="
            (index > 1 ? index / index : index <= 0 ? index : index - 0.5) + 0.5
          "
        />
      </section>
    </article>
    <Aside />
  </main>
</template>

<script>
import Header from "@/components/Basics/Header.vue";
import Project from "@/components/Project.vue";
import { projects } from "@/test.json";
import Aside from "@/components/Basics/Aside.vue";

export default {
  name: "Home",
  components: { Header, Project, Aside },
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
    setResponsiveSize() {
      const docWidth = document.body.clientWidth;
      if (docWidth >= 1449) this.perPage = 3;
      else if (docWidth <= 1448 && docWidth > 1015) this.perPage = 2;
      else this.perPage = 1;
    },
    getGithubProjects() {
      fetch("https://api.github.com/users/lenn-xsr/repos")
        .then((r) => r.json())
        .then((response) => {
          const projects = response.map(
            ({ id, name, description, url, language, stargazers_count }) => {
              return { id, name, description, url, language, stargazers_count };
            }
          );
          this.projects = [...this.projects, ...projects];
        });
    },
  },
  created() {
    this.getGithubProjects();
    this.setResponsiveSize();

    document.body.onresize = this.setResponsiveSize;
  },
};
</script>

<style scoped>
main {
  display: flex;
}

.projects-content {
  display: grid;
  overflow: hidden;
  width: 100%;
}

.project-wrapper {
  display: grid;
  place-content: center;
  justify-content: initial;
}

.projects-content .project-wrapper:not(:last-child) {
  border-right: 1px solid var(--fading);
  margin-right: -2px;
}

@media screen and (max-width: 1015px) {
  main {
    flex-direction: column;
  }
}
</style>