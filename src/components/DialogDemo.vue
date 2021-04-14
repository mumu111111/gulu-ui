<template>
  <div class="markdown-body">
    <h2>Dialog 弹框</h2>
    <p>
      需要用户处理事务，又不希望跳转页面以致打断工作流程时，可以使用 Dialog
      在当前页面正中打开一个浮层，承载相应的操作。
    </p>
    <div class="demo">
      <h2>支持 disabled</h2>
      <div class="demo-component">
        <component :is="Dialog1Demo"></component>
      </div>
      <div class="demo-actions">
        <Button @click="hideCode(1)" v-if="codeVisible">隐藏代码</Button>
        <Button @click="showCode(1)" v-else>查看代码</Button>
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
</template>

<script lang="ts">
import { ref } from "vue";
import Dialog1Demo from "./Dialog1.demo.vue";
import Dialog2Demo from "./Dialog2.demo.vue";
import Button from "../lib/Button.vue";
export default {
  setup() {
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
      Dialog1Demo,
      Dialog2Demo,
      showCode,
      hideCode,
      codeVisible,
      codeVisible1,
      Button,
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