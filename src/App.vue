<template>
  <a-layout id="app" style="min-height: 100%">
    <a-layout-sider
      :value="false"
      :trigger="null"
      collapsible
      :style="{ overflow: 'auto', height: '100vh', position: 'fixed', left: 0 }"
    >
      <div class="logo" />
      <a-menu theme="dark" mode="inline" :default-selected-keys="[defaultselecteditem]">
        <a-menu-item key="1" @click="$router.history.current.path!='/' && $router.push('/')">
          <a-icon type="book" />
          <span>Books</span>
        </a-menu-item>
        <a-menu-item key="2" @click="$router.history.current.path!='/favorite' && $router.push('/favorite')" >
          <a-icon type="star" />
          <span>Your favourites</span>
        </a-menu-item>
      </a-menu>
    </a-layout-sider>
    <a-layout style="margin-left: 200px">
      <a-layout-content style="flex-grow: 1;">
        <router-view/>
      </a-layout-content>
      <a-layout-footer>  </a-layout-footer>
    </a-layout>
  </a-layout>
</template>

<script>
import Vue from "vue";

import {Layout, Menu, Icon} from "ant-design-vue";
import "ant-design-vue/lib/menu/style/css";
import "ant-design-vue/lib/layout/style/css";
import "ant-design-vue/lib/icon/style/css";
Vue.use(Menu);
Vue.use(Layout);
Vue.use(Icon);


export default {
  name: "App",

  components: {},
  data() {
    return {
      defaultselecteditem: this.changeItem(),
    };
  },
  methods: {
    changeItem() {

      switch(window.location.pathname){
        case '/favorite': 
          return '2'
        case '/':
          return '1'
        default:
          return ''
      }
    }
  },

};

</script>

<style>
@import url('assets/tailwind.css');
</style>
