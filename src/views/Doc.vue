
<template>
  <div class="layout">
    <Topnav class="nav" toggleMenuButtonVisible />
    <div class="content">
      <aside v-if="asideVisible">
        <h2>文档</h2>
        <ol>
          <li>
            <router-link to="/doc/intro">介绍</router-link>
          </li>
        </ol>
        <h2>组件列表</h2>
        <ol>
          <li>
            <router-link to="/doc/switch">Switch 组件</router-link>
          </li>
          <li>
            <router-link to="/doc/button">Button 组件</router-link>
          </li>
          <li>
            <router-link to="/doc/dialog">Dialog 组件</router-link>
          </li>
          <li>
            <router-link to="/doc/tabs">Tabs 组件</router-link>
          </li>
        </ol>
      </aside>
      <main>
        <router-view></router-view>
      </main>
    </div>
  </div>
</template>

<script lang="ts">
import Topnav from "../components/Topnav.vue";
import { inject, Ref } from "vue";

export default {
  components: { Topnav },
  setup() {
    const asideVisible = inject<Ref<boolean>>("asideVisible"); // get
    console.log("doc获取标记", asideVisible.value);
    return { asideVisible };
  },
};
</script>
<style lang="scss" scoped>
$aside-index: 10;
.layout {
  display: flex;
  flex-direction: column;
  height: 100vh;
  > .nav {
    flex-shrink: 0;
  }
  > .content {
    flex-grow: 1;
    padding-top: 100px;
    padding-left: 156px;
    @media (max-width: 500px) {
      padding-left: 0;
    }
  }
}
.content {
  display: flex;
  > aside {
    flex-shrink: 0;
  }
  > main {
    flex-grow: 1;
    background: white;
    height: 100vh;
    overflow: auto;
    padding: 20px 25px;
  }
}
aside {
  background: #fff;
  width: 180px;
  padding: 100px 0px 0;
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  z-index: $aside-index;
  border-right: 1px solid #e8e8e8;
  > h2 {
    margin-bottom: 4px;
    padding: 4px 16px;
    font-size: 20px;
    font-weight: 700;
  }
  > ol {
    > li {
      > a {
        display: block;
        padding: 10px 30px;
        text-decoration: none;
        color: #333;
        font-size: 18px;
      }
      .router-link-active {
        background: white;
        color: green;
      }
    }
  }
}
main {
  overflow: auto;
}
</style> 
