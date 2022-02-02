<template>
  <div class="loading">
    <svg
      :width="width"
      :height="height"
      viewBox="0 0 50 50"
      preserveAspectRatio="xMidYMid meet"
    >
      <!--2pi * R / 4 -->
      <!-- stroke-linecap 定义圆角 方角 -->
      <circle
        cx="25"
        cy="25"
        r="22"
        fill="none"
        :stroke="outerColor"
        stroke-width="3"
        stroke-dasharray="34"
        stroke-linecap="round"
        transform-origin="25 25"
      >
        <!-- values 省略 from to -->
        <animateTransform
          attributeName="transform"
          attributeType="XML"
          type="rotate"
          values="0; 360"
          :dur="`${duration}s`"
          repeatCount="indefinite"
        ></animateTransform>
        <animate
          attributeName="stroke"
          :values="outsideColorAnimation"
          dur="4s"
          repeatCount="indefinite"
        ></animate>
      </circle>
      <circle
        cx="25"
        cy="25"
        r="12"
        fill="none"
        stroke-width="3"
        :stroke="innerColor"
        stroke-dasharray="19"
        stroke-linecap="round"
        transform-origin="25 25"
      >
        <animateTransform
          attributeName="transform"
          attributeType="XML"
          type="rotate"
          from="360"
          to="0"
          :dur="`${duration}s`"
          repeatCount="indefinite"
        ></animateTransform>
        <animate
          attributeName="stroke"
          :values="innerColorAnimation"
          dur="4s"
          repeatCount="indefinite"
        ></animate>
      </circle>
    </svg>
    <div class="loading-content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import { computed, onMounted } from "@vue/runtime-core";
export default {
  name: "Loading",
  props: {
    width: {
      type: [Number, String],
      default: 50,
    },
    height: {
      type: [Number, String],
      default: 50,
    },
    outerColor: {
      type: String,
      default: "#3be6",
    },
    innerColor: {
      type: String,
      default: "#02bc",
    },
    duration: {
      type: [Number, String],
      default: 2,
    },
  },
  setup(props) {
    const outsideColorAnimation = computed(() => {
      return `${props.outerColor};${props.innerColor};${props.outerColor}`;
    });
    const innerColorAnimation = computed(() => {
      return `${props.innerColor};${props.outerColor};${props.innerColor}`;
    });

    return {
      outsideColorAnimation,
      innerColorAnimation,
    };
  },
};
</script>
