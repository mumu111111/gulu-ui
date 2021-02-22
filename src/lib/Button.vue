<template>
  <button class="gulu-button" :class="classes" :disabled="disabled">
    <slot />
  </button>
</template>
<script lang="ts">
import { computed } from "vue";
export default {
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
    disabled: {
      type: Boolean,
      default: false,
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
$blue: #40a9ff;
$radius: 4px;
$red: red;
$grey: grey;
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
  &.gulu-theme-button {
    &[disabled] {
      cursor: not-allowed;
      color: $grey;
      &:hover {
        border-color: $grey;
      }
    }
  }
  &.gulu-theme-link,
  &.gulu-theme-text {
    &[disabled] {
      cursor: not-allowed;
      color: $grey;
    }
  }
}
</style>