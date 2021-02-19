<template>
  <router-view />
</template>

<script lang="ts">
import { ref, provide } from "vue";
import { router } from "./router";
export default {
  name: "App",

  setup() {
    // 声明变量标记  默认false
    const width = document.documentElement.clientWidth;

    const asideVisible = ref(width > 500 ? true : false);
    provide("asideVisible", asideVisible); // set
    // 设置手机端路由切换后 aside隐藏
    router.afterEach(() => {
      if (width <= 500) {
        asideVisible.value = false;
      }
    });
  },
};
</script>
