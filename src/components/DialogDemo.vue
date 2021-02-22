<template>
  <div>Dialog 示例</div>
  <Button @click="toggle">toggle</Button>
  <Dialog v-model:visible="x"></Dialog>
</template>
<script lang="ts">
import { ref } from "vue";
import Button from "../lib/Button.vue";
import Dialog from "../lib/Dialog.vue";
export default {
  components: { Dialog },
  setup() {
    const x = ref(false);
    const toggle = () => {
      x.value = !x.value;
    };
    return { x, toggle };
  },
};
</script>