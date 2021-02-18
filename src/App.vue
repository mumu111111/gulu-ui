<template>
  <router-view />
</template>

<script lang="ts">
import { ref, provide } from "vue";
export default {
  name: "App",

  setup() {
    // 声明变量标记  默认false
    console.log(2222);
    const asideVisible = ref(false);
    provide("xx", asideVisible); // set
  },
};
</script>
