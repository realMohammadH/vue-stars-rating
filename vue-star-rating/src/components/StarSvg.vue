<script setup>
import { defineProps } from "vue";

const props = defineProps({
  inactiveColor: {
    type: String,
    default: "#FFFFD0",
  },
  strokeWidth: {
    type: Number,
    default: 15,
  },
  strokeColor: {
    type: String,
    default: "#000",
  },
  strokeLinejoin: {
    type: String,
  },
  index: {
    type: Number,
  },
  starWidth: {
    type: Number,
    default: 50,
  },
  starHeight: {
    type: Number,
    default: 50,
  },
});
</script>

<template>
  <svg
    :data-star="index"
    class="star"
    version="1.1"
    x="0px"
    y="0px"
    :height="props.starHeight"
    :width="props.starWidth"
    :fill="props.inactiveColor"
    viewBox="0 0 512 512"
  >
    <polygon
      :stroke="props.strokeColor"
      :stroke-width="props.strokeWidth"
      :stroke-linejoin="props.strokeLinejoin"
      points="493.427,204.588 374.685,320.221 402.787,483.65 255.942,406.484 109.213,483.65 
	137.315,320.221 18.573,204.588 182.578,180.747 255.942,32.06 329.422,180.747 "
    />
  </svg>
</template>

<style scoped>
</style>
