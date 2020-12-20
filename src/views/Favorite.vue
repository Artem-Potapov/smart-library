<template>
  <div v-if="istest">Please, complete test!</div>
  <div v-else>I like ya cut g</div>
</template>

<script>
import Cookies from 'js-cookie'
export default {
  data() {
    return{
      istest: Cookies.get('test_complete') ? false: true
    }
  }
}
</script>

<style>

</style>