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
    level: {
      type: String,
      default: "normal",
    },
  },
  setup(props) {
    const { theme, size, level } = props;
    const classes = computed(() => {
      return {
        [`gulu-theme-${theme}`]: theme,
        [`gulu-theme-${size}`]: size,
        [`gulu-level-${level}`]: level,
      };
    });
    return { classes };
  },
};
</script>
<style lang="scss" scoped>
$blue: blue;
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
  &.gulu-theme-button {
    &.gulu-level-main {
      color: $blue;
      &:hover,
      &:focus {
        color: darken($blue, 10%);
      }
    }
    &.gulu-level-danger {
    }
  }
}
</style>