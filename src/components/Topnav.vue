<template>
  <div class="topnav">
    <router-link to="/" class="logo">
      <svg class="icon">
        <use xlink:href="#icon-xigua1"></use>
      </svg>
    </router-link>

    <ul class="menu">
      <li>
        <router-link to="/doc">文档</router-link>
      </li>
    </ul>
    <!-- <span class="toggleAside" @click="toggleMenu"></span> -->
    <svg v-if="toggleMenuButtonVisible" class="toggleAside" @click="toggleMenu">
      <use xlink:href="#icon-menu2"></use>
    </svg>
  </div>
</template>
<script lang="ts">
import { inject, Ref } from "vue";
export default {
  props: {
    toggleMenuButtonVisible: {
      type: Boolean,
      default: false,
    },
  },
  setup() {
    const asideVisible = inject<Ref<boolean>>("asideVisible"); // get
    console.log("topnav获取标记", asideVisible.value);
    const toggleMenu = () => {
      asideVisible.value = !asideVisible.value;
      console.log("topnav点击后", asideVisible.value);
    };
    return { toggleMenu };
  },
};
</script>
<style lang="scss" scoped>
/* $green: rgba(136, 225, 157, 0.61); */
$color: #007974;
$aside-index: 16;
.topnav {
  color: $color;
  /* background: $green; */
  display: flex;
  padding: 16px;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: $aside-index; //不被挡住
  box-shadow: 0 5px 5px rgb(51 51 51 / 10%);
  > .logo {
    max-width: 6em;
    margin-right: auto;
    > svg {
      width: 42px;
      height: 42px;
    }
  }
  > .menu {
    display: flex;
    align-items: center;
    white-space: nowrap;
    flex-wrap: nowrap;
    > li {
      margin: 0 1em;
    }
  }
  > .toggleAside {
    width: 21px;
    height: 21px;
    /* background: red; */
    position: absolute;
    left: 16px;
    top: 50%;
    transform: translateY(-50%);
    display: none;
    /* background: fade-out(black, 0.9); */
  }
  @media (max-width: 500px) {
    > .menu {
      display: none;
    }
    > .logo {
      margin: 0 auto;
    }
    > .toggleAside {
      display: inline-block;
    }
  }
}
</style>
