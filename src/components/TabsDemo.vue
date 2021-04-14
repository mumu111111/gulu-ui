<template>
  <div class="markdown-body">
    <h2>Tabs 标签页</h2>
    <p>选项内容切换</p>
    <div class="demo">
      <h2>常规用法</h2>
      <div class="demo-component">
        <component :is="Tabs1Demo"></component>
      </div>
      <div class="demo-actions">
        <Button @click="hideCode(1)" v-if="codeVisible">隐藏代码</Button>
        <Button @click="showCode(1)" v-else>查看代码</Button>
      </div>
      <div class="demo-code" v-if="codeVisible">
        <pre><code>
&lt;template&gt;
  &lt;Tabs v-model:selected="selected" &gt;
    &lt;Tab title="导航1"&gt;内容1&lt;/Tab&gt;
    &lt;Tab title="导航2"&gt;内容2&lt;/Tab&gt;
    &lt;Tab title="导航3"&gt;内容3&lt;/Tab&gt;
  &lt;/Tabs&gt;
&lt;/template&gt;
&lt;script lang="ts"&gt;
import Tabs from "../lib/Tabs.vue";
import Tab from "../lib/Tab.vue";
import {ref} from 'vue';
export default {
  components:{Tabs,Tab},
  setup(){
    const selected = ref('导航1')
    return {selected}
  }
}
&lt;/script&gt;
   
   </code></pre>
      </div>
    </div>
    <div class="demo">
      <h2>支持disabled</h2>
      <div class="demo-component">
        <component :is="Tabs2Demo"></component>
      </div>
      <div class="demo-actions">
        <Button @click="hideCode(2)" v-if="codeVisible1">隐藏代码</Button>
        <Button @click="showCode(2)" v-else>查看代码</Button>
      </div>
      <div class="demo-code" v-if="codeVisible1">
        <pre><code>
&lt;template&gt;
  &lt;Tabs v-model:selected="selected" :disabled="disabled" &gt;
    &lt;Tab title="导航1"&gt;内容1&lt;/Tab&gt;
    &lt;Tab title="导航2"&gt;内容2&lt;/Tab&gt;
    &lt;Tab title="导航3"&gt;内容3&lt;/Tab&gt;
  &lt;/Tabs&gt;
&lt;/template&gt;
&lt;script lang="ts"&gt;
import Tabs from "../lib/Tabs.vue";
import Tab from "../lib/Tab.vue";
import {ref} from 'vue';
export default {
  components:{Tabs, Tab},
  setup(){
    const selected = ref('导航1')
    const disabled = ref(['导航2'])
    return {selected, disabled}
  }
}
&lt;/script&gt;
   
   </code></pre>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import Tabs1Demo from "./Tabs1.demo.vue";
import Tabs2Demo from "./Tabs2.demo.vue";
import { ref } from "vue";
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
      Tabs1Demo,
      Tabs2Demo,
      codeVisible,
      codeVisible1,
      showCode,
      hideCode,
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