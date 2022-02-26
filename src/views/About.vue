<template>
  <section class="page about">
    <h2 class="page__title">
      <span>About</span>
    </h2>

    <div class="about__inner">
      <!-- <div class="about__image">
        <img src="../assets/images/me/eun1.png" alt="" class="img1" />
        <img src="../assets/images/me/eun3.jpeg" alt="" class="img2" />
        <img src="../assets/images/me/eun4.jpeg" alt="" class="img3" />
      </div> -->
      <div class="about__profile">
        <div class="about__item">
          <h3 class="title">
            <span class="icon material-icons-round"> badge </span>
            <span class="text">내 정보</span>
          </h3>
          <p class="descr">
            이정은<br />
            1992.01.31<br />
            010-2737-2394<br />
            qoo0131@naver.com<br />
          </p>

          <a href="https://github.com/eun92" target="_blank" class="link">
            <img src="@/assets/images/icon/github.png" />
          </a>
        </div>
        <div class="about__item">
          <h3 class="title">
            <span class="icon material-icons-round"> history_edu </span>
            <span class="text">학력</span>
          </h3>
          <p class="descr">
            2015.06 ~ 2015.09 더조은컴퓨터학원 (NCS)모바일 앱 UI/UX디자인
            훈련과정 수료 <br />
            2010.03 ~ 2014.02 강원대학교 영어영문학과 졸업<br />
            2007.03 ~ 2010.02 북원여자고등학교 졸업
          </p>
        </div>
        <div class="about__item">
          <h3 class="title">
            <span class="icon material-icons-round"> work_history </span>
            <span class="text">경력</span>
          </h3>
          <p class="descr">
            2018.07 ~ 2021.08 리마커블소프트 재직<br />
            2015.10 ~ 2018.03 인포아트커뮤니케이션 재직
          </p>
        </div>
        <div class="about__item">
          <h3 class="title">
            <span class="icon material-icons-round">
              integration_instructions
            </span>
            <span class="text">SKILL</span>
          </h3>
          <!-- <p class="descr">
            html5, css3, scss, javascript, vue js, nuxt js, git, jquery,
            크로스브라우징, 반응형
          </p> -->
          <ul class="icon-group">
            <li>
              <img src="@/assets/images/icon/html5.png" />
            </li>
            <li>
              <img src="@/assets/images/icon/css3.png" />
            </li>
            <li>
              <img src="@/assets/images/icon/sass.png" />
            </li>
            <li>
              <img src="@/assets/images/icon/js.png" />
            </li>
            <li>
              <img src="@/assets/images/icon/vue.png" />
            </li>
            <li>
              <img src="@/assets/images/icon/nuxt.png" />
            </li>
            <li>
              <img src="@/assets/images/icon/git.png" />
            </li>
            <li>
              <img src="@/assets/images/icon/github.png" />
            </li>
            <li>
              <span>크로스 브라우징</span>
            </li>
            <li>
              <span>반응형</span>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.about {
  &__inner {
    @include flexbox();
    // background: #fff;
    // padding: rem(30);
    border-radius: rem(20);
  }

  &__image {
    position: relative;
    flex: 1;
    @include flexbox($jc: center);
    flex-wrap: wrap;

    img {
      border: rem(5) solid $primary;
      border-radius: rem(30);

      &.img1 {
        width: rem(156);
        height: rem(200);
      }

      &.img2 {
        width: rem(200);
        height: rem(200);
      }

      &.img3 {
        width: rem(355);
        height: rem(240);
      }
    }
  }

  &__profile {
    position: relative;
    flex: 1.5;
    @include flexbox($ai: stretch);
    flex-wrap: wrap;
  }

  &__item {
    position: relative;
    width: 48%;
    margin: 1%;
    padding: rem(20);
    background: #fff;
    border-radius: rem(15);

    @include animation(
      $animationName: fadeIn,
      $animationDelay: 0.3s,
      $animationDuration: 0.8s
    );

    .link {
      position: absolute;
      bottom: rem(5);
      right: rem(10);

      img {
        width: rem(28);
      }
    }

    .title {
      display: inline-flex;
      align-items: center;
      margin-bottom: rem(5);
      font-size: rem(18);
      font-weight: 400;
      font-family: "HoengseongHanu", "sans-serif";
      @include after-mark-text($h: 35%, $bg: $point);

      .icon {
        margin-right: rem(3);
        font-size: rem(21);
      }
    }
  }

  .icon-group {
    @include flexbox();
    flex-wrap: wrap;

    > li {
      padding: rem(5);

      img {
        width: rem(30);
      }
    }
  }
}

@include mobile() {
  .about__item {
    width: 100%;
  }
}
</style>
