<template>
  <div style="display:flex;">
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

  </div>
</template>

<script>
import Vue from "vue";
import { Button, Card, Icon, Rate } from "ant-design-vue";
import "ant-design-vue/lib/button/style/css";
import "ant-design-vue/lib/card/style/css";
import "ant-design-vue/lib/icon/style/css";
import "ant-design-vue/lib/rate/style/css";
Vue.use(Button);
Vue.use(Card);
Vue.use(Icon);
Vue.use(Rate);


export default {
  name: 'Home',
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

}
</script>
