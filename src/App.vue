<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!-- <svg-animation></svg-animation> -->
  <loading :width="120" :height="120" :duration="2.5">
    <div style="font-size: 20px; color: #333">数据加载中...</div>
  </loading>
  <fly-box></fly-box>
</template>

<script>
import SvgAnimation from "./components/SvgAnimation/SvgAnimation";
import Loading from "./components/icon/Loading/Loading.vue";
import FlyBox from "./components/icon/FlyBox/FlyBox.vue";
export default {
  name: "App",
  components: {
    SvgAnimation,
    Loading,
    FlyBox,
  },
};
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
