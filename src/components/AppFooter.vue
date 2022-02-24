<template>
  <footer class="footer">
    <a href="https://github.com/eun92" target="_blank">
      &copy; {{ new Date().getFullYear() }} Jeongeun
    </a>
  </footer>
</template>

<script>
export default {}
</script>

<style lang="scss">
.footer {
  margin: auto auto 0;
  padding: rem(40) 0;

  a {
    text-transform: uppercase;
  }
}
</style>
