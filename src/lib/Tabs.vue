<template>
  <div>
    tabs组件
    <component :is="defaults[0]"></component>
    <component :is="defaults[1]"></component>
  </div>
</template>
<script>
import Tab from "./Tab.vue";
export default {
  setup(props, context) {
    console.log(context);
    const defaults = context.slots.default();
    console.log(defaults);
    defaults.forEach((tag) => {
      console.log(tag.type);
      //   检查子组件类型
      if (tag.type !== Tab) {
        throw new Error("Tabs 子标签必须时 Tab");
      }
    });
    return { defaults };
  },
};
</script>