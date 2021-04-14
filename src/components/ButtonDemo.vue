<template>
  <div class="markdown-body">
    <h1>Button 按钮</h1>
    <h3></h3>
    <p>支持不同需求下的按钮，响应用户点击行为，触发相应的业务逻辑</p>
    <div class="demo">
      <h2>常规用法</h2>
      <div class="demo-component">
        <component :is="Button1Demo"></component>
      </div>
      <div class="demo-actions">
        <Button @click="hideCode(0)" v-if="codeVisible">隐藏代码</Button>
        <Button @click="showCode(0)" v-else>查看代码</Button>
      </div>
      <div class="demo-code" v-if="codeVisible">
        <pre><code>
&lt;template&gt;
  &lt;Button theme="button"&gt; 普通按钮 &lt;/Button&gt;
  &lt;Button theme="link"&gt;链接按钮 &lt;/Button&gt;
  &lt;Button theme="text"&gt; 文本按钮 &lt;/Button&gt;
&lt;/template>

&lt;script lang="ts" &gt;
import {Button} from '../lib/Button.vue';
export default {
  components:{ Button }
}
&lt;/script&gt;
   </code></pre>
      </div>
    </div>
    <div class="demo">
      <h2>支持size</h2>
      <div class="demo-component">
        <component :is="Button2Demo"></component>
      </div>
      <div class="demo-actions">
        <Button @click="hideCode(1)" v-if="codeVisible1">隐藏代码</Button>
        <Button @click="showCode(1)" v-else>查看代码</Button>
      </div>
      <div class="demo-code" v-if="codeVisible1">
        <pre><code>
&lt;template&gt;
  &lt;Button  size="big"&gt; 大按钮 &lt;/Button&gt;
  &lt;Button &gt;普通按钮 &lt;/Button&gt;
  &lt;Button  size="small"&gt; 小按钮 &lt;/Button&gt;
&lt;/template>

&lt;script lang="ts" &gt;
import {Button} from '../lib/Button.vue';

export default {
  components:{ Button }
}
&lt;/script&gt;
   </code></pre>
      </div>
    </div>
    <div class="demo">
      <h2>支持level</h2>
      <div class="demo-component">
        <component :is="Button3Demo"></component>
      </div>
      <div class="demo-actions">
        <Button @click="hideCode(2)" v-if="codeVisible2">隐藏代码</Button>
        <Button @click="showCode(2)" v-else>查看代码</Button>
      </div>
      <div class="demo-code" v-if="codeVisible2">
        <pre><code>
&lt;template&gt;
  &lt;Button theme="button" level="main"&gt; 主要按钮 &lt;/Button&gt;
  &lt;Button theme="button" &gt;普通按钮 &lt;/Button&gt;
  &lt;Button theme="button" level="danger"&gt; 危险按钮 &lt;/Button&gt;
&lt;/template>

&lt;script lang="ts" &gt;
import {Button} from '../lib/Button.vue';

export default {
  components:{ Button }
}
&lt;/script&gt;
   </code></pre>
      </div>
    </div>
    <div class="demo">
      <h2>支持禁用</h2>
      <div class="demo-component">
        <component :is="Button4Demo"></component>
      </div>
      <div class="demo-actions">
        <Button @click="hideCode(3)" v-if="codeVisible3">隐藏代码</Button>
        <Button @click="showCode(3)" v-else>查看代码</Button>
      </div>
      <div class="demo-code" v-if="codeVisible3">
        <pre><code>
&lt;template&gt;
  &lt;Button theme="button" disabled&gt; 普通禁用按钮 &lt;/Button&gt;
  &lt;Button theme="link" disabled&gt;链接禁用按钮 &lt;/Button&gt;
  &lt;Button theme="text" disabled&gt; 文本禁用按钮 &lt;/Button&gt;
&lt;/template>

&lt;script lang="ts" &gt;
import {Button} from '../lib/Button.vue';

export default {
  components:{ Button }
}
&lt;/script&gt;
   </code></pre>
      </div>
    </div>
    <div class="demo">
      <h2>支持loading</h2>
      <div class="demo-component">
        <component :is="Button5Demo"></component>
      </div>
      <div class="demo-actions">
        <Button @click="hideCode(4)" v-if="codeVisible4">隐藏代码</Button>
        <Button @click="showCode(4)" v-else>查看代码</Button>
      </div>
      <div class="demo-code" v-if="codeVisible4">
        <pre><code>
&lt;template&gt;
  &lt;Button theme="button"  loading &gt; 加载中 &lt;/Button&gt;
  &lt;Button theme="button"&gt;加载完毕 &lt;/Button&gt;
&lt;/template>

&lt;script lang="ts" &gt;
import {Button} from '../lib/Button.vue';

export default {
  components:{ Button }
}
&lt;/script&gt;
   </code></pre>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { ref } from "vue";
import Button from "../lib/Button.vue";
import Button1Demo from "./Button1.demo.vue";
import Button2Demo from "./Button2.demo.vue";
import Button3Demo from "./Button3.demo.vue";
import Button4Demo from "./Button4.demo.vue";
import Button5Demo from "./Button5.demo.vue";
export default {
  setup() {
    const showCode = (t) => {
      if (t == 0) {
        codeVisible.value = true;
      } else if (t == 1) {
        codeVisible1.value = true;
      } else if (t == 2) {
        codeVisible2.value = true;
      } else if (t == 3) {
        codeVisible3.value = true;
      } else if (t == 4) {
        codeVisible4.value = true;
      }
    };
    const hideCode = (t) => {
      if (t == 0) {
        codeVisible.value = false;
      } else if (t == 1) {
        codeVisible1.value = false;
      } else if (t == 2) {
        codeVisible2.value = false;
      } else if (t == 3) {
        codeVisible3.value = false;
      } else if (t == 4) {
        codeVisible4.value = false;
      }
    };
    const codeVisible = ref(false);
    const codeVisible1 = ref(false);
    const codeVisible2 = ref(false);
    const codeVisible3 = ref(false);
    const codeVisible4 = ref(false);

    return {
      Button,
      Button1Demo,
      Button2Demo,
      Button3Demo,
      Button4Demo,
      Button5Demo,
      showCode,
      hideCode,
      codeVisible,
      codeVisible1,
      codeVisible2,
      codeVisible3,
      codeVisible4,
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
    margin-top: 0;
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