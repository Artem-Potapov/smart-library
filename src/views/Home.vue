<template>
  <div style="display: flex">
    <div style="display: flex; flex-grow: 1; padding: 30px">
      <a-card
        hoverable
        style="
          width: 200px;
          margin-left: 20px;
          margin-right: 20px;
          height: 450px;
        "
        v-for="book in books"
        :key="book.name"
      >
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
          download="123"
          size="small"
          >download</a-button
        >
      </a-card>
    </div>
    <div
      style="
        padding: 10px
        width: 200px;
        background: white;
        box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.1);
      "
    >
      <h4><b>Автор:</b></h4>
      <a-select style="align-self: flex-start; width: 200px">
        <a-select-option
          :value="author"
          v-for="author in authors"
          :key="author"
        >
          {{ author }}
        </a-select-option>
      </a-select>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import { Button, Card, Icon, Rate, Select } from "ant-design-vue";
import "ant-design-vue/lib/button/style/css";
import "ant-design-vue/lib/card/style/css";
import "ant-design-vue/lib/icon/style/css";
import "ant-design-vue/lib/rate/style/css";
import "ant-design-vue/lib/select/style/css";

Vue.use(Button);
Vue.use(Card);
Vue.use(Icon);
Vue.use(Rate);
Vue.use(Select);

export default {
  name: "Home",
  mounted() {
    this.$axios.get("http://localhost:5000").then((res) => {
      this.books = res.data;
    });
    this.$axios.get("http://localhost:5000/authors").then((res) => {
      this.authors = res.data;
    });
  },
  components: {},
  data() {
    return {
      size: "large",
      desc: ["1", "2", "3", "4", "5"],
      books: [],
      authors: [],
    };
  },
};
</script>
