<template>
  <a-layout id="app" style="min-height: 100%">
    <a-layout-sider
      v-model="collapsed"
      :trigger="null"
      collapsible
      :style="{ overflow: 'auto', height: '100vh', position: 'fixed', left: 0 }"
    >
      <div class="logo" />
      <a-menu theme="dark" mode="inline" :default-selected-keys="['1']">
        <a-menu-item key="1">
          <a-icon type="user" />
          <span>nav 1</span>
        </a-menu-item>
        <a-menu-item key="2">
          <a-icon type="video-camera" />
          <span>nav 2</span>
        </a-menu-item>
        <a-menu-item key="3">
          <a-icon type="upload" />
          <span>nav 3</span>
        </a-menu-item>
      </a-menu>
    </a-layout-sider>
    <a-layout style="margin-left: 200px">
      <a-layout-content style="flex-grow: 1">
        <router-view />
      </a-layout-content>
      <a-layout-footer> Footer </a-layout-footer>
    </a-layout>
  </a-layout>
</template>

<script>
import Vue from "vue";
import { Button, Card, Layout, Menu, Icon } from "ant-design-vue";
import "ant-design-vue/lib/button/style/css";
import "ant-design-vue/lib/menu/style/css";
import "ant-design-vue/lib/layout/style/css";
import "ant-design-vue/lib/card/style/css";
import "ant-design-vue/lib/icon/style/css";
Vue.use(Button);
Vue.use(Menu);
Vue.use(Card);
Vue.use(Layout);
Vue.use(Icon);

export default {
  name: "App",
  mounted() {
    this.$axios.get('http://localhost:5000').then((res) => {
      console.log(res.data)
    })
  },
  components: {},
  data() {
    return {
      users: [],
    };
  },
};
</script>

<style>
</style>
