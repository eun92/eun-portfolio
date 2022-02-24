<template>
  <div class="project">
    <div class="project__inner">
      <div
        v-if="item.image"
        class="project__image"
        :style="{
          background:
            'url(' +
            require('../assets/images/project/' + item.image) +
            ') 50% 0% no-repeat',
        }"
      ></div>
      <div class="project__description">
        <ul class="descr-list">
          <li>
            <h3 class="project__title" v-text="item.name">
              <!-- 세계 국기 퀴즈 -->
            </h3>
            <p class="descr" v-text="item.description">
              <!-- 세계 국기 이미지를 보고 국가명을 맞추는 미니 게임 -->
            </p>
          </li>
          <li v-if="item.mainFunction">
            <span class="title">주요 기능</span>
            <ul class="descr">
              <li
                v-for="(item, index) in item.mainFunction"
                :key="index"
                v-text="item"
              ></li>
            </ul>
          </li>
          <li v-if="item.workingPeriod">
            <span class="title">작업기간</span>
            <p class="descr" v-text="item.workingPeriod">
              <!-- 2022.02 ~ 2022.02. -->
            </p>
          </li>
          <li>
            <span class="title">Skills</span>
            <p class="descr" v-text="item.skills">
              <!-- vue, scss,-->
            </p>
          </li>
          <li>
            <div class="project__links">
              <a :href="item.github" target="_blank" v-if="item.github"
                >Github</a
              >
              <a :href="item.notion" target="_blank" v-if="item.notion"
                >Notion</a
              >
              <a :href="item.url" target="_blank" v-if="item.url">URL</a>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import ScrollMagic from "scrollmagic"

export default {
  props: {
    item: {
      type: Object,
    },
  },
  data() {
    return {}
  },
  mounted() {
    this.onScroll()
  },
  methods: {
    onScroll() {
      const controller = new ScrollMagic.Controller()
      const animationItems = document.querySelectorAll(".project")

      animationItems.forEach((item) => {
        new ScrollMagic.Scene({
          triggerElement: item, //각 요소가 트리거가 됨
          offset: 30,
          triggerHook: 0.9,
        })
          .setClassToggle(item, "visible") //해당 요소에 클래스 토글
          .addTo(controller)
      })
    },
  },
}
</script>

<style lang="scss" scoped>
.project {
  width: $projectWsize;
  padding: $projectSpace;
  background-size: 100% !important;
  transform: translateX(-30px);
  opacity: 0;
  transition: all 0.3s;

  &.visible {
    opacity: 1;
    transform: translateX(0);
  }

  &__title {
    display: inline-block;
    margin-bottom: rem(5);
    font-size: rem(20);
    font-family: "HoengseongHanu", "sans-serif";
    @include after-mark-text($h: 35%, $bg: $point);
  }

  &__inner {
    overflow: hidden;
    position: relative;
    @include flexbox($ai: start);
    height: 100%;
    min-height: rem(280);
    padding: rem(20);
    background: #fff;
    transition: 0.3s;
    border-radius: rem(30);

    &:hover {
      transform: translateY(-#{rem(5)});
      @include box-shadow-default();

      .project__image {
        transform: translateY(105%);
      }
    }
  }

  &__image {
    @include after-bg($w: 100%, $h: 100%, $bg: rgba(255, 255, 255, 0.12));
    position: absolute;
    top: 0;
    left: 0;
    z-index: 20;
    width: 100%;
    height: 100%;
    background-size: cover !important;
    transition: 0.5s;
  }

  &__description {
    // flex: 1;
    flex-grow: 1;
  }

  .descr-list {
    > li {
      margin: rem(10);

      .title {
        font-weight: 700;
      }

      .descr {
        text-transform: uppercase;
        > li {
          position: relative;
          margin: rem(3) 0;
          padding-left: rem(10);

          &::after {
            @include pseudo-selector(
              $w: rem(5),
              $h: rem(5),
              $bg: darken($primary, 20%)
            );
            border-radius: 50%;
            position: absolute;
            left: 0;
            top: rem(9);
            // @include pos-center-y();
          }
        }
      }
    }
  }

  &__links {
    a {
      padding: rem(5) rem(10);
      background: $second;
      border-radius: rem(30);
      font-size: rem(15);
      font-family: "Godo", "sans-serif";
      transition: 0.3s;

      &:hover {
        background: $primary;
      }

      + a {
        margin-left: rem(5);
      }
    }
  }
}
</style>
