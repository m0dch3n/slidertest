<script setup lang="ts">
import Slider from "@vueform/slider";
import { ref } from "vue";
import { DateTime } from "luxon";

const val = ref([8.5, 12, 13, 18, 19, 22]);
const format = (value: number) => {
  const beforeDecimal = Math.floor(value);
  const afterDecimal = value - beforeDecimal;
  const hour = beforeDecimal;
  const minute = Math.round(60 * afterDecimal);
  const time = DateTime.fromObject({ hour, minute });
  return `${time.toLocaleString(DateTime.TIME_SIMPLE)}`;
};
</script>
<template>
  <div class="p-8 pt-20">
    <Slider v-model="val" :min="0" :max="24" :step="0.25" :format="format" />
  </div>
</template>

<style src="@vueform/slider/themes/default.css"></style>
