<template>
  <div class="gulu-tabs">
    <div class="gulu-tabs-nav" ref="container">
      <div
        class="gulu-tabs-nav-item"
        v-for="(t, index) in titles"
        :ref="
          (el) => {
            if (t == selected) {
              selectItem = el;
            }
          }
        "
        :key="index"
        :class="{ selected: t == selected }"
        :style="
          disabled.indexOf(t) >= 0 ? 'cursor: not-allowed' : 'cursor:pointer'
        "
        @click="select(t)"
      >
        {{ t }}
      </div>
      <div class="gulu-tabs-nav-indicator" ref="indicator"></div>
    </div>
    <div class="gulu-tabs-content">
      <component
        class="gulu-tabs-content-item"
        :class="{ selected: c.props.title == selected }"
        v-for="(c, index) in defaults"
        :is="c"
        :key="index"
      />
    </div>
  </div>
</template>
<script lang="ts">
import { onMounted, onUpdated, ref, watchEffect, computed } from "vue";
import Tab from "./Tab.vue";
export default {
  props: {
    selected: {
      type: String,
    },
    disabled: {
      type: Array,
      default: [],
    },
  },
  setup(props, context) {
    const selectItem = ref<HTMLDivElement>(null);
    const indicator = ref<HTMLDivElement>(null);
    const container = ref<HTMLDivElement>(null);

    onMounted(() => {
      // 当第一次渲染后才能获取到selectItem
      watchEffect(() => {
        console.log(selectItem.value);
        const { width } = selectItem.value.getBoundingClientRect(); // 导航的宽度
        indicator.value.style.width = width + "px"; // 动态获取width
        const { left: left1 } = container.value.getBoundingClientRect();
        const { left: left2 } = selectItem.value.getBoundingClientRect();
        const left = left2 - left1;
        indicator.value.style.left = left + "px";
      });
    });
    const defaults = context.slots.default();
    defaults.forEach((tag) => {
      //   检查子组件类型
      console.log("tag", tag);
      console.log("Tab", Tab);

      // if (tag.type !== Tab) {
      if (tag.type.name !== Tab.name) {
        throw new Error("Tabs 子标签必须时 Tab");
      }
    });
    const titles = defaults.map((tag) => {
      return tag.props.title;
    });
    const select = (title: string) => {
      if (props.disabled.indexOf(title) < 0) {
        context.emit("update:selected", title);
        console.log(
          "2223222222",
          defaults.filter((item) => item.props.title === title)[0]
        );
        return defaults.filter((item) => item.props.title === title)[0];
      }
    };
    // const current = computed(() => {
    //   return select(props.selected);
    // });
    // const select = (t) => {
    //   context.emit("update:selected", t);
    // };
    return { defaults, titles, select, selectItem, indicator, container };
  },
};
</script>
<style lang="scss">
$blue: #40a9ff;
$color: #333;
$border-color: #d9d9d9;
.gulu-tabs {
  &-nav {
    display: flex;
    color: $color;
    border-bottom: 1px solid $border-color;
    position: relative;
    &-item {
      padding: 8px 0;
      margin: 0 16px;
      cursor: pointer;
      &:first-child {
        margin-left: 0;
      }
      &.selected {
        color: $blue;
      }
    }
    &-indicator {
      position: absolute;
      height: 3px;
      background: $blue;
      left: 0;
      bottom: -1px;
      width: 100px;
      transition: all 250ms;
    }
  }
  &-content {
    padding: 8px 0;
    &-item {
      display: none;
      &.selected {
        display: block;
      }
    }
  }
}
</style>