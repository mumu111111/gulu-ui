<template>
  <div>
    <button class="gulu-button" :class="classes">
      <slot />
    </button>
  </div>
</template>
<script lang="ts">
import { computed } from "vue";
export default {
  inheritAttrs: false,
  props: {
    theme: {
      type: String,
      default: "button",
    },
    size: {
      type: String,
      default: "normal",
    },
  },
  setup(props) {
    const { theme, size } = props;
    const classes = computed(() => {
      return {
        [`gulu-theme-${theme}`]: theme,
        [`gulu-theme-${size}`]: size,
      };
    });
    return { classes };
  },
};
</script>
<style lang="scss" scoped>
.gulu-button {
  &.gulu-theme-link {
    border: 1px solid red;
  }
  &.gulu-theme-text {
  }
  &.gulu-theme-button {
  }
  &.gulu-size-small {
  }
  &.gulu-size-big {
  }
  &.gulu-size-normal {
  }
}
</style>