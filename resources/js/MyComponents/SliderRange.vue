<template>
  <input
    id="myinput"
    type="range"
    value="0"
    min="0"
    max="60"
    class="range-slider"
    @input="updateRangeBackground"
  >
</template>

<script setup>
const updateRangeBackground = (event) => {
  const range = event.target;
  const value = (range.value - range.min) / (range.max - range.min) * 100;
  range.style.background = `linear-gradient(to right, #C87A2C 0%, #C87A2C ${value}%, #fff ${value}%, white 100%)`;
};

// Initial background setup on component mount (optional)
// This ensures the correct initial background when the page reloads or the component mounts
import { onMounted } from 'vue';

onMounted(() => {
  const range = document.getElementById('myinput');
  const value = (range.value - range.min) / (range.max - range.min) * 100;
  range.style.background = `linear-gradient(to right, #C87A2C 0%, #C87A2C ${value}%, #cfcfcf ${value}%, #cfcfcf 100%)`;
});
</script>

<style scoped>
#myinput {
  background: linear-gradient(to right, #C87A2C 0%, #cfcfcf 0%, #cfcfcf 100%);
  border: solid 1px #cfcfcf;
  border-radius: 8px;
  height: 15px;
  width: 100%;
  outline: none;
  transition: background 450ms ease-in;
  -webkit-appearance: none;
}

input[type=range]::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 30px; /* Thumb width */
  height: 30px; /* Thumb height */
  border-radius: 50%;
  background: #fff; /* Thumb color */
  cursor: pointer;
  box-shadow: 2px 2px 5px #797979;
}
</style>
