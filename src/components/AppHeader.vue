<template>
  <header class="header">
    <div class="header__inner">
      <h1 class="header__title">
        <!-- <span>Jeongeun's</span>
        <span class="indent-text">Portfolio</span> -->
        <router-link to="/">Jeongeun's Portfolio</router-link>
      </h1>
      <div class="header__links">
        <router-link to="/"> Home </router-link>
        <router-link to="/history"> History </router-link>
        <router-link to="/about"> About </router-link>
      </div>
    </div>
  </header>
</template>

<script>
export default {}
</script>

<style lang="scss">
.header {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 900;
  width: 100%;
  height: $headerHeight;
  transition: 0.3s;

  &.is-scroll {
    position: fixed;
    // background: darken($primary, 20%);
    background: #333;
    @include box-shadow-default();

    .header__inner {
      align-items: center;
    }

    // * {
    //   color: #000;
    // }
  }

  &__inner {
    @include flexbox($jc: between);
    @include w-margin-auto();
    height: 100%;
  }

  &__title {
    margin-right: rem(10);
    font-size: rem(25);
    line-height: 1;
    font-family: "Staatliches", "sans-serif";
    color: #fff;
    letter-spacing: 1.1px;

    .indent-text {
      display: block;
      text-indent: rem(79);
    }
  }

  &__links {
    @include flexbox();

    a {
      text-transform: uppercase;
      position: relative;
      color: #fff;
      font-family: "realway", "sans-serif";

      + a {
        padding-left: rem(20);

        &:after {
          @include pseudo-selector($w: 1px, $h: 50%, $bg: #fff);
          @include pos-center-y();
          left: rem(10);
        }
      }

      &:hover,
      &:focus,
      &.router-link-exact-active {
        color: $primary;
      }

      img {
        max-height: 100%;
      }
    }
  }
}
</style>
