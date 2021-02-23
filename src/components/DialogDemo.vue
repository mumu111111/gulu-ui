<template>
  <div>Dialog 示例</div>
  <Button @click="toggle">toggle</Button>
  <Dialog
    v-model:visible="x"
    :closeOnclickOverlay="false"
    :ok="f1"
    :cancel="f2"
  ></Dialog>
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
    const f1 = () => {
      console.log("f1");
      return false;
    };
    const f2 = () => {
      console.log("f2");
    };

    return { x, toggle, f1, f2 };
  },
};
</script>
