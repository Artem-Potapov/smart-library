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
          <a-icon type="book" />
          <span>Books</span>
        </a-menu-item>
        <a-menu-item key="2">
          <a-icon type="user" />
          <span>Profile</span>
        </a-menu-item>
        <a-menu-item key="3">
          <a-icon type="star" />
          <span>Your favourites</span>
        </a-menu-item>
      </a-menu>
    </a-layout-sider>

    <a-layout style="margin-left: 200px">
      <a-layout-content style="flex-grow: 1; padding: 30px; display: flex">
        <router-view/>
        <a-card hoverable style="width: 200px; margin-left: 20px; margin-right: 20px; height:450px" v-for="book in books" :key='book.name' >
          <img
            slot="cover"
            alt="example"
            :src="book.img"
          />
          <a-card-meta :title="book.name">
            <template slot="description">{{book.author}}</template>
          </a-card-meta>
          <a-rate v-model="book.rate" :tooltips="desc" allow-half disabled/>
          <a-button :href='book.download' type="link" shape="round" icon="download" download='123' size="small">download</a-button>
        </a-card>
      </a-layout-content>
      <a-layout-footer> Footer </a-layout-footer>
    </a-layout>
  </a-layout>
</template>

<script>
import Vue from "vue";

import { Button, Card, Layout, Menu, Icon, Rate } from "ant-design-vue";
import "ant-design-vue/lib/button/style/css";
import "ant-design-vue/lib/menu/style/css";
import "ant-design-vue/lib/layout/style/css";
import "ant-design-vue/lib/card/style/css";
import "ant-design-vue/lib/icon/style/css";
import "ant-design-vue/lib/rate/style/css";
Vue.use(Button);
Vue.use(Menu);
Vue.use(Card);
Vue.use(Layout);
Vue.use(Icon);
Vue.use(Rate);

export default {
  name: "App",
  mounted(){
    const xhr = new XMLHttpRequest()
    xhr.open('GET', 'http://localhost:5000')
    xhr.send()
    xhr.onload = () => {
      if (xhr.readyState != 4) return
      this.books = JSON.parse(xhr.response)
    }
  },
  components: {},
  data() {
    return {
      size: 'large',
      desc: ["1", "2", "3", "4", "5"],
      books: [],
    };
  },
  methods: {
      handleSizeChange(e) {
        this.size = e.target.value;
      },
    },

};

</script>

<style>
</style>
