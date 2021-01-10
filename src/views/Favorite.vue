<template>
  <test @testdone="istest=false" v-if="istest"/>
  <favorite-list v-else/>
</template>

<script>
import FavoriteList from "../components/FavoriteList";
import Test from "../components/Test"
import Cookies from "js-cookie"

export default {
  
  data() {
    return {
      istest: Cookies.get("result") ? false : true,
    };
  },
  components: {
    FavoriteList,
    Test
  },

};
</script>