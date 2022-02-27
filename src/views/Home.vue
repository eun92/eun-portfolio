<template>
  <section class="page home">
    <h2 class="page__title">
      <span>Toy Project</span>
    </h2>

    <p class="page__descr">
      프론트엔드 기술을 최대한 활용하여 만들어 본 토이 프로젝트입니다.<br />
      노션에 더 자세한 기술 관련 설명이 있습니다.<br />
      URL은 무료 호스팅 사이트를 이용해서 접속이 느릴 수 있습니다. (초기 로딩
      오래 걸림)
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
