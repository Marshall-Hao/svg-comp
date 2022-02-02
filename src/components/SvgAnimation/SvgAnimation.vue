<template>
  <div class="container">
    <svg width="500" height="200" viewBox="0 0 500 200">
      <!-- 
            [2, -1, 50] => newX = oldX*2 + oldY*(-1) + 50
            [1, 2, 0] => newY = oldX * 1 + oldY * (2) + 0
         -->
      <!-- transform="matrix(2 1 -1 2 50 0)" -->
      <rect
        class="rect"
        x="5"
        y="5"
        width="100"
        height="50"
        fill="none"
        stroke-width="5"
        stroke="blue"
      />
    </svg>
  </div>
  <div class="container">
    <svg width="50" height="50" viewBox="0 0 400 400">
      <circle
        cx="200"
        cy="200"
        r="180"
        stroke-width="20"
        stroke="#d1d3d7"
        fill="transparent"
      ></circle>
      <!-- 2Pi.180 -->
      <circle
        class="circle"
        cx="200"
        cy="200"
        r="180"
        stroke-width="20"
        stroke="#00a5e0"
        fill="none"
        transform-origin="200 200"
        transform="rotate(-90)"
      ></circle>
    </svg>
  </div>
  <div class="container">
    <svg width="200" height="200" viewBox="0 0 200 200">
      <rect
        x="0"
        y="0"
        width="200"
        height="200"
        fill="none"
        stroke="grey"
        stroke-width="8"
      ></rect>
      <rect
        x="0"
        y="0"
        width="200"
        height="200"
        fill="none"
        stroke="blue"
        stroke-width="8"
        class="rect-animation"
        transform="matrix(0,1,-1,0,200,0)"
      ></rect>
    </svg>
  </div>
</template>

<script>
export default {
  name: "svg-animation",
};
</script>

<style lang="scss" scoped>
.container {
  svg {
    border: 1px solid #000;
    .rect {
      // * 10线段 20空白 30线段 。。。
      stroke-dasharray: 10 20 30;
    }
    .circle {
      stroke-dasharray: 10 1131;
      animation: circle 5s linear infinite;
    }
    .rect-animation {
      stroke-dasharray: 10 800;
      animation: rect 5s linear infinite;
    }
  }
}

@keyframes circle {
  from {
    stroke-dasharray: 0 1131;
  }
  to {
    stroke-dasharray: 1131 0;
  }
}

@keyframes rect {
  from {
    stroke-dasharray: 0 800;
  }
  to {
    stroke-dasharray: 800 0;
  }
}
</style>
