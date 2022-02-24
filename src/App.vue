<template>
  <div id="app">
    <div class="container">
      <app-header id="header"></app-header>
      <app-visual></app-visual>
      <div class="content">
        <router-view />
      </div>
      <app-footer></app-footer>
    </div>
    <button type="button" id="to-top" @click="onClickToTop()">
      <span class="material-icons">arrow_upward</span>
    </button>
  </div>
</template>

<script>
import AppHeader from "@/components/AppHeader.vue"
import AppFooter from "@/components/AppFooter.vue"
import AppVisual from "./components/AppVisual.vue"
import gsap from "gsap"
import { ScrollToPlugin } from "gsap/all"
gsap.registerPlugin(ScrollToPlugin)

export default {
  components: {
    AppHeader,
    AppFooter,
    AppVisual,
  },
  mounted() {
    this.onScroll()
  },
  methods: {
    onScroll() {
      const toTopEl = document.querySelector("#to-top")
      // const header = document.querySelector("#header")

      window.addEventListener("scroll", function () {
        if (window.scrollY > 100) {
          // 버튼 보이기
          gsap.to(toTopEl, 0.2, {
            opacity: 1,
            display: "flex",
            x: 0,
          })

          // header.classList.add("is-scroll")
        } else {
          // 버튼 숨기기
          gsap.to(toTopEl, 0.2, {
            opacity: 0,
            display: "none",
            x: 100,
          })
          // header.classList.remove("is-scroll")
        }
      })
    },

    onClickToTop() {
      gsap.to(window, 0.7, {
        scrollTo: 0,
      })
    },
  },
}
</script>

<style lang="scss">
html,
body,
#app {
  width: 100%;
  height: 100%;
}

html {
  font-size: 16px;
}

body {
  font-family: "Noto Sans KR", sans-serif;
  color: #333;
  background: $primary;
}

#app {
  min-width: 280px;
}

.container {
  display: flex;
  flex-direction: column;
  position: relative;
  min-height: 100%;
  // padding: rem(40) rem(30);
}

.content {
  @include w-margin-auto();
  padding: rem(30) $defaulPadding;

  .page {
    &__title {
      @include flexbox($jc: center);
      margin: rem(20) 0;

      span {
        position: relative;
        padding-left: rem(20);
        font-size: rem(35);
        line-height: 1;
        font-weight: 700;
        font-family: "Nunito", "sans-serif";
        z-index: 10;

        &::after {
          @include pseudo-selector(
            $w: rem(25),
            $h: rem(25),
            $bg: darken($primary, 20%)
          );

          position: absolute;
          left: #{rem(11)};
          top: -#{rem(8)};
          z-index: -1;
          border-radius: rem(5);
        }
      }
    }

    &__descr {
      margin: rem(10) 0;
      text-align: center;
      color: #000;
      background: darken($primary, 20%);
      padding: rem(10);
      border-radius: rem(8);
    }
  }

  .projects {
    @include flexbox($ai: stretch);
    flex-wrap: wrap;
  }
}

$toTopSize: rem(42);
$toTopPosition: rem(30);

#to-top {
  position: fixed;
  bottom: $toTopPosition;
  right: $toTopPosition;
  z-index: 9;
  @include flexbox($jc: center);
  opacity: 0;
  width: $toTopSize;
  height: $toTopSize;
  background-color: #333;
  color: #fff;
  border: rem(2) solid #fff;
  border-radius: rem(10);
  cursor: pointer;
}

@include laptop-sm() {
  html {
    font-size: 13px;
  }
}

@include mobile() {
  html {
    font-size: 11px;
  }

  .projects {
    .project {
      width: 100% !important;
      transition-delay: initial !important;
      padding: 2% 0 !important;

      &__inner {
        border-radius: rem(10) !important;
      }
    }
  }
}
</style>

<style>
/* icon font  */
@import "https://fonts.googleapis.com/css?family=Material+Icons|Material+Icons+Outlined|Material+Icons+Two+Tone|Material+Icons+Round|Material+Icons+Sharp";
/* fonts */
@import "https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100;300;400;500;700;900&family=Raleway:wght@200;300;400;500;700;900&family=Nunito:wght@400;500&family=Staatliches&display=swap";
</style>
