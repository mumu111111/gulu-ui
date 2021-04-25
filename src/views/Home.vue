
<template>
  <div>
    <div class="topnavAndBanner">
      <Topnav />
      <div class="banner">
        <h1>COKE-UI</h1>
        <h2>简单，好用</h2>
        <p class="actions">
          <a href="https://github.com/mumu111111">GitHub</a>
          <router-link to="/doc">开始</router-link>
        </p>
      </div>
    </div>
    <div class="features">
      <ul>
        <li>
          <svg>
            <use xlink:href="#icon-vue"></use>
          </svg>
          <h3>基于 Vue 3</h3>
          <p>使用了 Vue 3 Composition API</p>
        </li>
        <li>
          <svg>
            <use xlink:href="#icon-ts"></use>
          </svg>
          <h3>基于 TypeScript</h3>
          <p>源代码采用 TypeScript 书写</p>
        </li>
        <li>
          <svg>
            <use xlink:href="#icon-light"></use>
          </svg>
          <h3>代码易读</h3>
          <p>每个组件的源代码都极其简洁</p>
        </li>
      </ul>
    </div>
  </div>
</template>
<script lang="ts">
import Topnav from "../components/Topnav.vue";
export default {
  components: { Topnav },
};
</script>
<style lang="scss" scoped>
$green: rgb(90, 180, 176);
$border-radius: 4px;
$color: #007974;
.topnavAndBanner {
  background: linear-gradient(
    145deg,
    rgb(111, 200, 132) 0%,
    rgb(213, 255, 223) 100%
  );
  clip-path: ellipse(80% 60% at 50% 40%);
}
.features {
  margin: 64px auto;
  padding: 0 16px;
  @media (min-width: 800px) {
    width: 800px;
    > ul {
      > li {
        width: 50%;
      }
    }
  }
  @media (min-width: 1200px) {
    width: 1200px;
    > ul {
      > li {
        width: 33.3333%;
      }
    }
  }

  > ul {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    > li {
      width: 300px;
      margin: 16px 0;
      display: grid;
      justify-content: start;
      align-content: space-between;
      grid-template-areas:
        "icon title"
        "icon text";
      grid-template-columns: 80px auto;
      grid-template-rows: 1fr auto;
      > svg {
        grid-area: icon;
        width: 64px;
        height: 64px;
      }
      > h3 {
        grid-area: title;
        font-size: 28px;
      }
      > p {
        grid-area: text;
      }
    }
  }
}

.banner {
  color: $color;
  padding: 110px 0px 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  > .actions {
    padding: 20px 0;
    a {
      margin: 0px 10px;
      background: $green;
      color: white;
      $h: 28px;
      height: $h;
      line-height: $h;
      border-radius: $h/2;
      padding: 8px 26px;
      border-radius: $border-radius;
      &:hover {
        text-decoration: none;
      }
    }
  }
}
</style>