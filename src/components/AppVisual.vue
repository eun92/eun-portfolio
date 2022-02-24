<template>
  <div class="visual">
    <div class="visual__inner">
      <div class="visual__text">FRONT-END DEVELOPER</div>
      <div class="visual__image">
        <img src="@/assets/images/me/eun2.jpeg" />
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.visual {
  width: 100%;
  height: rem(250);
  padding-top: $headerHeight;
  background: url(../assets/images/bg/laptop.jpg) 50% 130% no-repeat;
  background-size: cover;
  background-attachment: fixed;
  @include after-bg();

  &__inner {
    position: relative;
    z-index: 10;
    @include w-margin-auto();
    height: 100%;
    @include flexbox($jc: center);
  }

  &__text {
    color: $primary;
    font-size: rem(50);
    font-weight: 300;
    line-height: 1;
    font-family: "realway", "sans-serif";
    text-align: center;
  }

  &__image {
    $imageSize: rem(230);
    @include after-bg($bg: rgba(255, 255, 255, 0.08));
    overflow: hidden;
    position: absolute;
    top: 25%;
    right: $defaulPadding;
    width: $imageSize;
    height: $imageSize;
    border: rem(10) solid $primary;
    border-radius: rem(50);

    a {
      display: block;
    }

    img {
      width: 100%;
      transition: 0.3s;
    }

    &:hover {
      &::after {
        background: transparent;
        transition: 0.3s;
      }

      img {
        transform: scale(1.1);
      }
    }
  }
}

@include laptop-sm() {
  .visual__text {
    font-size: rem(35);
  }
}

@include tablet-ver() {
  .visual__image {
    display: none;
  }
}
</style>
