<template>
  <div>
    <div class="markdown-body">
      <h1>Switch 示例</h1>
      <div class="demo">
        <h2>常规用法</h2>
        <div class="demo-component">
          <component :is="Switch1Demo"></component>
        </div>
        <div class="demo-actions">
          <Button @click="hideCode(1)" v-if="codeVisible">隐藏代码</Button>
          <Button @click="showCode(1)" v-else>查看代码</Button>
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
      <div class="demo">
        <h2>支持 disabled</h2>
        <div class="demo-component">
          <!-- <Switch2Demo /> -->
          <component :is="Switch2Demo"></component>
        </div>
        <div class="demo-actions">
          <Button @click="hideCode(2)" v-if="codeVisible1">隐藏代码</Button>
          <Button @click="showCode(2)" v-else>查看代码</Button>
        </div>
        <div class="demo-code" v-if="codeVisible1">
          <pre><code>&lt;template&gt;
  &lt;Switch v-model:value="bool"  disabled /&gt;
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
  </div>
</template>
<script lang="ts">
import Switch from "../lib/Swtich.vue";
import Button from "../lib/Button.vue";
import Switch1Demo from "./Switch1.demo.vue";
import Switch2Demo from "./Switch2.demo.vue";
import { ref } from "vue";
export default {
  components: {
    Switch1Demo,
    Switch2Demo,
    Switch,
    Button,
  },
  setup() {
    const bool = ref(false);
    const showCode = (t) => {
      if (t == 1) {
        codeVisible.value = true;
      } else {
        codeVisible1.value = true;
      }
    };
    const hideCode = (t) => {
      if (t == 1) {
        codeVisible.value = false;
      } else {
        codeVisible1.value = false;
      }
    };
    const codeVisible = ref(false);
    const codeVisible1 = ref(false);

    return {
      bool,
      Switch1Demo,
      Switch2Demo,
      showCode,
      hideCode,
      codeVisible,
      codeVisible1,
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