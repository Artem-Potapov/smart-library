<template>
  <div class='flex-wrap flex flex-grow p-8'>
    <a-card
      hoverable
      style="
        width: 200px;
        margin-left: 20px;
        margin-right: 20px;
        margin-bottom: 30px;
        height: 450px;"
      v-for="book in books"
      :key="book.name">
      <img slot="cover" alt="example" :src="book.img" />
      <a-card-meta :title="book.name">
        <template slot="description">{{ book.author }}</template>
      </a-card-meta>
      <a-rate v-model="book.rate" :tooltips="desc" allow-half disabled />
      <a-button
        :href="book.download"
        type="link"
        shape="round"
        icon="download"
        size="small"
        >download</a-button
      >
    </a-card>
  </div>
</template>

<script>
import Vue from "vue";
import {Rate} from "ant-design-vue";
import 'ant-design-vue/lib/rate/style/css'
import Cookie from 'js-cookie'
Vue.use(Rate)
export default {
  mounted() {
    this.$axios.get("http://localhost:5000/favbooks", {
      params: {
        testresult: Cookie.get('result')
      }
    }).then((res) => {
      this.books = res.data;
    });
  },
  data() {
    return {
      books: [],
      desc: [],
    };
  },
  methods: {},
};
</script>

<style>

</style>