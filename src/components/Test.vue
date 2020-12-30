<template>
<div>
    <a-card style="margin: 30px">
      <span slot="title" :class="{ error: iserror && !genres.length }"
        >Какой жанр вам нравится?</span
      >
      <a-checkbox @change="(e) => onChange(e, 'povest')">Повесть</a-checkbox>
      <a-checkbox @change="(e) => onChange(e, 'tale')">Сказка</a-checkbox>
      <a-checkbox @change="(e) => onChange(e, 'roman')">Роман</a-checkbox>
      <a-checkbox @change="(e) => onChange(e, 'all')">Я не знаю</a-checkbox>
    </a-card>
    <a-card style="margin: 30px">
      <span slot="title" :class="{ error: iserror && !age }"
        >В какую возраснтую категорию вы входите?</span
      >
      <a-radio-group v-model="age">
        <a-radio :value="6"> 6+ </a-radio>
        <a-radio :value="10"> 10+ </a-radio>
        <a-radio :value="12"> 12+ </a-radio>
        <a-radio :value="16"> 16+ </a-radio>
      </a-radio-group>
    </a-card>
    <a-card style="margin: 30px">
      <span slot="title" :class="{ error: iserror && !capacity }"
        >Какой обьем страниц для вас приемлем?</span
      >
      <a-radio-group v-model="capacity">
        <a-radio :value="50"> До 50 </a-radio>
        <a-radio :value="100"> До 100 </a-radio>
        <a-radio :value="200"> До 200 </a-radio>
        <a-radio :value="400"> До 400 </a-radio>
        <a-radio :value="Number.MAX_VALUE"> Мне не важен обьём </a-radio>
      </a-radio-group>
    </a-card>
    <a-card style="margin: 30px">
      <span slot="title" :class="{ error: iserror && !authors.length }"
        >Какие авторы вам больше по душе?</span
      >
      <a-checkbox
        @change="(e) => authorChange(e, author)"
        v-for="author in allAuthors"
        :key="author"
        >{{ author }}</a-checkbox
      >
    </a-card>
    <a-button type="primary" style="margin: 0px 30px" @click="okay"
      >ОК</a-button
    >
  </div>
</template>

<script>
import Vue from "vue";
import { Card, Radio, Checkbox, Button } from "ant-design-vue";
import "ant-design-vue/lib/card/style/css";
import "ant-design-vue/lib/radio/style/css";
import "ant-design-vue/lib/checkbox/style/css";
import "ant-design-vue/lib/button/style/css";
import Cookies from "js-cookie";
Vue.use(Card);
Vue.use(Radio);
Vue.use(Checkbox);
Vue.use(Button);
export default {
  name: 'Test'
}
</script>

<style>

</style>