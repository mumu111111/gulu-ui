<template>
  <div class="markdown-body">
    <h1>Tabs 示例</h1>
    <div class="demo">
      <h2>常规用法</h2>
      <div class="demo-component">
        <component :is="Tabs1Demo"></component>
      </div>
      <div class="demo-actions">
        <Button @click="hideCode" v-if="codeVisible">隐藏代码</Button>
        <Button @click="showCode" v-else>查看代码</Button>
      </div>
      <div class="demo-code" v-if="codeVisible">
        <pre><code>&lt;template&gt;
  &lt;Switch v-model:value="bool" /&gt;
&lt;/template&gt;
&lt;script lang="ts"&gt;
import Switch from "../lib/Swtich.vue";
import { ref } from "vue";
export default {
  components: {
    Switch,
  },
  setup() {
    const bool = ref(false);
    return {
      bool,
    };
  },
};
&lt;/script&gt;
 </code></pre>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import Button from "../lib/Button.vue";
import Tabs1Demo from "./Tabs1.demo.vue";
import { ref } from "vue";
export default {
  setup() {
    const showCode = () => (codeVisible.value = true);
    const hideCode = () => (codeVisible.value = false);
    const codeVisible = ref(false);
    return {
      Button,
      Tabs1Demo,
      codeVisible,
      showCode,
      hideCode,
    };
  },
};
</script>
<style lang="scss" scoped>
$border-color: #d9d9d9;
.demo {
  border: 1px solid $border-color;
  margin: 16px 0 32px;
  > h2 {
    margin-top: 0px;
    font-size: 20px;
    padding: 8px 16px;
    border-bottom: 1px solid $border-color;
  }
  &-component {
    padding: 16px;
  }
  &-actions {
    padding: 8px 16px;
    border-top: 1px dashed $border-color;
  }
  &-code {
    padding: 8px 16px;
    border-top: 1px dashed $border-color;
    > pre {
      line-height: 1.1;
      font-family: Consolas, "Courier New", Courier, monospace;
      margin: 0;
    }
  }
}
</style>