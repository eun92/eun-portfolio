<template>
  <section class="page history">
    <h2 class="page__title">
      <span>History</span>
    </h2>

    <p class="page__descr">
      퍼블리싱 및 스타일에 관련된 스크립트 작업을 위주로 했던 프로젝트입니다.<br />
      웹화면만 있는 것들은 대부분 반응형으로 작업했으며, 참여도는 대부분 80%
      이상입니다.<br />
      URL은 접속 가능한 사이트만 기재했습니다.
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
import json from "../data/historyProjects.json"

export default {
  name: "Home",
  components: { ProjectItem },
  data() {
    return {
      projects: json.projects,
    }
  },
  created() {
    // console.log(json.projects)
  },
  methods: {},
}
</script>

<style lang="scss" scoped>
.project {
  width: 33.33333%;

  &:nth-child(3n -1) {
    transition-delay: 0.2s;
  }

  &:nth-child(3n) {
    transition-delay: 0.4s;
  }
}

@include tablet-hor() {
  .project {
    width: 50%;

    &:nth-child(3n -1) {
      transition-delay: 0s;
    }

    &:nth-child(3n) {
      transition-delay: 0s;
    }

    &:nth-child(2n) {
      transition-delay: 0.2s;
    }

    &__inner {
      min-height: rem(350);
    }
  }
}
</style>
