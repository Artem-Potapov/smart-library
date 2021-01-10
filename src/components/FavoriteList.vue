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
        >download</a-button>
    </a-card>
    <a-button href='http://localhost:8080/favorite' type='primary' shape='round' @click="reTest()">Перепройти тест</a-button>
  </div>
</template>

<script>
import Vue from "vue";
import {Rate} from "ant-design-vue";
import 'ant-design-vue/lib/rate/style/css'
import Cookies from 'js-cookie'


Vue.use(Rate)
export default {
  mounted() {
    this.$axios.get("http://localhost:5000/favbooks", {
      params: {
        testresult: Cookies.get('result')
      }
    }).then((res) => {
      this.books = res.data;
    });
  },
  data() {
    return {
      books: [],
      desc: [],
      showtest: Cookies.get('result') ? false : true
    };
  },
  methods: {
    reTest(){
      Cookies.remove('result')
      this.$emit('retest')
      
    }
  },
  components: {
  
  }
};
</script>

<style>

</style>