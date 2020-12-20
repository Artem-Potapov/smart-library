<template>
  <div v-if="istest">
    <a-card title="Вопрос номер 1" style="margin: 30px">
      <a-radio-group v-model="value">
        <a-radio :value="1"> A </a-radio>
        <a-radio :value="2"> B </a-radio>
        <a-radio :value="3"> C </a-radio>
        <a-radio :value="4"> D </a-radio>
      </a-radio-group>
    </a-card>
    <a-card title="Вопрос номер 2" style="margin: 30px">
      <a-radio-group v-model="value">
        <a-radio :value="1"> A </a-radio>
        <a-radio :value="2"> B </a-radio>
        <a-radio :value="3"> C </a-radio>
        <a-radio :value="4"> D </a-radio>
      </a-radio-group>
    </a-card>
    <a-card title="Вопрос номер 3" style="margin: 30px">
      <a-radio-group v-model="value">
        <a-radio :value="1"> A </a-radio>
        <a-radio :value="2"> B </a-radio>
        <a-radio :value="3"> C </a-radio>
        <a-radio :value="4"> D </a-radio>
      </a-radio-group>
    </a-card>
  </div>
  <div v-else>I like ya cut g</div>
</template>

<script>
import Vue from "vue";
import { Card, Radio } from "ant-design-vue";
import "ant-design-vue/lib/card/style/css";
import "ant-design-vue/lib/radio/style/css";
import Cookies from "js-cookie";
Vue.use(Card);
Vue.use(Radio);

export default {
  data() {
    return {
      value: "",
      istest: Cookies.get("test_complete") ? false : true,
    };
  },
};
</script>

<style>
</style>