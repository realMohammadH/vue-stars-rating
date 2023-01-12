<script setup>
import { ref, defineProps, computed, onMounted } from "vue";
import StarSvg from "./StarSvg.vue";

const stars = ref([]);
const

const props = defineProps({
  StarCount: {
    type: Number,
    default: 5,
  },
  gap: {
    type: Number,
    default: 0.2,
  },
  StarsFlow: {
    type: String,
    default: "row",
  },
  activeColor: {
    type: String,
    default: "#ffe272",
  },
  readOnly: {
    type: Boolean,
    default: false,
  },
  maxActiveStars: {
    type: Number,
    default: 0,
    required: false,
  },
});

function addStarActive() {
  stars.value.forEach((star, index) => {
    const elem = star.$el;
    elem.addEventListener("click", () => {
      stars.value.forEach((elem) => {
        elem.$el.classList.add("active");
      });
      stars.value.slice(index + 1, stars.value.length).forEach((elem) => {
        elem.$el.classList.remove("active");
      });
      = ref(document.querySelectorAll(".active").length);
    });
  });
}

function maxActiveStars() {
  stars.value.slice(0, props.maxActiveStars).forEach((star) => {
    star.$el.classList.add("active");
  });
}

if (props.readOnly === true) {
  onMounted(maxActiveStars);
} else {
  onMounted(addStarActive);
}

const Gap = computed(function () {
  return props.gap + "rem";
});
</script>

<template>
  <div
    class="stars-container"
    :style="{ gap: Gap, flexDirection: props.StarsFlow }"
  >
    <star-svg
      ref="stars"
      v-bind="$attrs"
      v-for="s in props.StarCount"
      :key="s"
      :id="s"
      :star-height="50"
      :star-width="50"
    ></star-svg>
    <span class="ratingNum"> {{ activeStarsCount }} </span>
  </div>
</template>

<style scoped>
.stars-container {
  display: flex;
  padding: 0.5rem;
  width: fit-content;
  align-items: center;
}
.active {
  fill: v-bind("props.activeColor") !important;
}
.ratingNum {
  display: block;
  font-size: 2.8rem;
  font-weight: 900;
  padding: 0 0 0 0.5rem;
}
</style>