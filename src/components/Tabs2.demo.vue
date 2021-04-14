<template>
  <Tabs v-model:selected="selected" :disabled="disabled">
    <Tab title="导航1">内容1</Tab>
    <Tab title="导航2">内容2</Tab>
    <Tab title="导航3">内容3</Tab>
  </Tabs>
</template>

<script lang="ts">
import Tabs from "../lib/Tabs.vue";
import Tab from "../lib/Tab.vue";
import { ref } from "vue";
export default {
  components: { Tabs, Tab },
  setup() {
    console.log("eeeeeeeee");
    const selected = ref("导航1");
    const disabled = ref(["导航2"]);
    return { selected, disabled };
  },
};
</script>