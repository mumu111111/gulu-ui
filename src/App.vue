<template>
  <router-view />
</template>

<script lang="ts">
import { ref, provide } from "vue";
export default {
  name: "App",

  setup() {
    // 声明变量标记  默认false
    const width = document.documentElement.clientWidth;

    const asideVisible = ref(width > 500 ? true : false);
    provide("xx", asideVisible); // set
  },
};
</script>
