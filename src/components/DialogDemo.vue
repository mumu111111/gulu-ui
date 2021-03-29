<template>
  <h1>Dialog 示例</h1>
  <div class="demo">
    <h2>支持 disabled</h2>
    <div class="demo-component">
      <component :is="Dialog1Demo"></component>
    </div>
    <div class="demo-actions">
      <Button @click="hideCode" v-if="codeVisible">隐藏代码</Button>
      <Button @click="showCode" v-else>查看代码</Button>
    </div>
    <div class="demo-code" v-if="codeVisible">
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

  <div class="demo">
    <h2>支持 disabled</h2>
    <div class="demo-component">
      <component :is="Dialog2Demo"></component>
    </div>
    <div class="demo-actions">
      <Button @click="hideCode" v-if="codeVisible">隐藏代码</Button>
      <Button @click="showCode" v-else>查看代码</Button>
    </div>
    <div class="demo-code" v-if="codeVisible">
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
</template>

<script lang="ts">
import Button from "../lib/Button.vue";
import Dialog1Demo from "./Dialog1.demo.vue";
import Dialog2Demo from "./Dialog2.demo.vue";
export default {
  setup() {
    return {
      Button,
      Dialog1Demo,
      Dialog2Demo,
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