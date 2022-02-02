<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <svg-animation></svg-animation>
</template>

<script>
import SvgAnimation from "./components/SvgAnimation/SvgAnimation"
export default {
  name: 'App',
  components: {
    SvgAnimation
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>