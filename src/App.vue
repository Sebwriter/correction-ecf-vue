<template>
  <div id="app">
    <router-view />
    <FooterView />
  </div>
</template>


<script>

import FooterView from '@/components/FooterView.vue'

export default {
  name:"App",
  components:{
    FooterView
  }
}
</script>

<style>
@import url("@/assets/css/main.css")
</style>
