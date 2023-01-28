<template>
  <div>
    <Slider v-model="value" :max="max" :on-change="change(value)"></Slider>
  </div>
</template>

<script setup lang="ts">
import {} from "vue";
</script>
<script lang="ts">
export default {
  data() {
    return {
      value: 25,
      max: 300,
    };
  },
  onMounted: {},
  methods: {
    change(val: number) {
      console.log(val);
    },
  },
};
</script>

<style scoped lange="less"></style>
