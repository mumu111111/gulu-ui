
<template>
  <Button disabled>普通禁用</Button>
  <Button theme="link" disabled>链接禁用</Button>
  <Button theme="text" disabled>文本禁用</Button>
</template>

<script lang="ts">
import Button from "../lib/Button.vue";
export default {
  components: {
    Button,
  },
};
</script>