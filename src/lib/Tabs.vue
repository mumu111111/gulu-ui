<template>
  <div>
    <div v-for="(title, index) in titles" key="index">{{ title }}</div>
    <component v-for="(c, index) in defaults" :is="c" key="index" />
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
    const titles = defaults.map((tag) => {
      return tag.props.title;
    });
    return { defaults, titles };
  },
};
</script>