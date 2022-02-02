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
  <div class="container">
    <svg viewBox="0 0 1024 1024" width="200" height="200">
      <path
        ref="logoRef"
        class="logo"
        d="M840.9088 736.3072H296.9088c-30.9248 0-57.5488-23.0912-61.8496-53.76L158.9248 142.3872c-0.0512-0.512-0.512-0.8704-1.024-0.8704H53.0432v-61.44h104.8576c30.976 0 57.5488 23.0912 61.8496 53.76l11.8272 84.1216h690.7904c18.8928 0 36.5568 8.3968 48.4352 23.04 11.9296 14.6432 16.5888 33.6384 12.7488 52.1216l-81.4592 393.3696c-5.9392 28.8768-31.6928 49.8176-61.184 49.8176zM240.2816 279.3984l55.6032 394.5472c0.0512 0.512 0.512 0.9216 1.024 0.9216h544c0.512 0 0.9216-0.3584 1.024-0.8192l81.4592-393.3696c0.0512-0.2048 0.1024-0.4608-0.2048-0.8704-0.3072-0.4096-0.6144-0.4096-0.8192-0.4096H240.2816zM353.8432 948.9408c-48.64 0-88.2176-39.5776-88.2176-88.2176s39.5776-88.2176 88.2176-88.2176 88.2176 39.5776 88.2176 88.2176-39.5776 88.2176-88.2176 88.2176z m0-115.0464c-14.7968 0-26.7776 12.032-26.7776 26.7776 0 14.7968 12.032 26.7776 26.7776 26.7776 14.7968 0 26.7776-12.032 26.7776-26.7776a26.8288 26.8288 0 0 0-26.7776-26.7776zM786.944 948.9408c-48.64 0-88.2176-39.5776-88.2176-88.2176s39.5776-88.2176 88.2176-88.2176 88.2176 39.5776 88.2176 88.2176-39.5776 88.2176-88.2176 88.2176z m0-115.0464c-14.7968 0-26.7776 12.032-26.7776 26.7776 0 14.7968 12.032 26.7776 26.7776 26.7776 14.7968 0 26.7776-12.032 26.7776-26.7776a26.8288 26.8288 0 0 0-26.7776-26.7776z"
        fill="#4D5254"
        p-id="20245"
      ></path>
      <path
        d="M384 534.3232h381.2352v61.44H384z"
        fill="#00A0E9"
        p-id="20246"
      ></path>
    </svg>
  </div>
</template>

<script>
import { onMounted, ref } from "vue";

export default {
  name: "svg-animation",
  setup() {
    const logoRef = ref(null);
    onMounted(() => {
      const logoLength = logoRef.value.getTotalLength();
      console.log(logoLength);
    });
    // console.log(logoRef.value);
    return {
      logoRef,
    };
  },
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
    .logo {
      fill: none;
      stroke: #333;
      stroke-width: 5;
      animation: logo 5s linear 1 forwards;
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

@keyframes logo {
  0% {
    fill: white;
    stroke-dasharray: 6391;
    stroke-dashoffset: 6391;
  }
  50% {
    fill: white;
    stroke-dasharray: 6391;
    stroke-dashoffset: 0;
  }
  75% {
    fill: red;
  }
  100% {
    fill: blue;
  }
}
</style>
