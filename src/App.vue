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
      <a-button type="link" shape="round" icon="download" size="small">download</a-button>
      <a-layout-content style="flex-grow: 1; padding: 30px; display: flex">
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
          <a-button href='https://github.com/Artem-Potapov/Vse_Skazki/archive/_.zip' type="link" shape="round" icon="download" size="small">download</a-button>
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
  components: {},
  data() {
    return {
      size: 'large',
      desc: ["1", "2", "3", "4", "5"],
      books: [
        { name: "Детство", author: "Л.Н.Толстой", img: 'https://1.bp.blogspot.com/-wWUjjNPVA30/XV7O6j0NwsI/AAAAAAAAAIk/a9zxrJFhPbAvhoReUPvrylLhXpoEAbAjACLcBGAs/s1600/3eb7fe8839702db7e1dd1133a873e8cb.jpg', rate: 4.5 },
        { name: "Церная курица", author: "Антоний Погорельский", img: 'https://7960777a-2fd1-4b07-8bbb-896e98c4659c.selcdn.net/upload/prod_add4/961/product-360961-1.jpg', rate: 4 },
        { name: "В дурном обществе", author: "Владимир Короленко",img: 'https://kapital-knigi.ru/assets/images/products/11893/9785222321089.jpg', rate: 5},
      ],
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
