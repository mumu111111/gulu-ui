<template>
  <button @click="toggle" :class="{ 'gulu-checked': value }">
    <span></span>
  </button>
</template>
<script>
import { ref } from "vue";
export default {
  props: { value: Boolean },
  setup(props, context) {
    const checked = ref(false);
    const toggle = () => {
      context.emit("update:value", !props.value);
    };
    return { checked, toggle };
  },
};
</script>
<style lang="scss" scoped>
$h: 22px;
$h2: $h - 4px;
button {
  height: $h;
  width: $h * 2;
  border: none;
  background: #bfbfbf;
  border-radius: $h/2;
  position: relative;
  &.gulu-checked {
    background: #1890ff;
  }
  &.gulu-checked > span {
    left: calc(100% - #{$h2} - 2px);
  }
  &:focus {
    outline: none;
  }
  /* 激活时span形状变化 */
  &:active {
    > span {
      width: $h2 + 4px;
    }
  }
  &.gulu-checked:active {
    > span {
      width: $h2 + 4px;
      margin-left: -4px;
    }
  }
  &[disabled] {
    cursor: not-allowed;
  }
}

span {
  position: absolute;
  top: 2px;
  left: 2px;
  height: $h2;
  width: $h2;
  background: white;
  border-radius: $h2 / 2;
  transition: all 250ms;
}
</style> 