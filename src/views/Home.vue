<template>
  <section class="page home">
    <h2 class="page__title">
      <span>Toy Project</span>
    </h2>

    <p class="page__descr">
      프론트엔드 기술을 최대한 활용하여 만들어 본 토이 프로젝트입니다.
    </p>

    <div class="projects">
      <project-item
        v-for="(item, index) in projects"
        :key="index"
        :item="item"
      ></project-item>
    </div>
  </section>
</template>

<script>
import ProjectItem from "../components/ProjectItem.vue"
import json from "../data/toyProjects.json"

export default {
  name: "Home",
  components: { ProjectItem },
  data() {
    return {
      projects: json.projects,
    }
  },
  created() {},
  mounted() {},
  methods: {},
}
</script>

<style lang="scss" scoped>
.project {
  &:nth-child(2n) {
    transition-delay: 0.3s;
  }
}
</style>
