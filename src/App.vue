<template>
  <div id="app">
    <router-view />
    <FooterGuide v-show="$route.meta.showFooter" />
  </div>
</template>

<script>
import FooterGuide from './components/FooterGuide/FooterGuide.vue'
// import { reqAddress } from './api'
// import { reqFoodTypes } from './api'
import { mapActions } from 'vuex'

export default {
  // async mounted() {
  //   const result = await reqFoodTypes()
  //   console.log(result)
  // },第一次测试
  mounted() {
    // this.$store.dispatch('getAddress') // 和下面一样效果的方法
    this.getAddress()
  },

  methods: {
    ...mapActions(['getAddress'])
  },

  components: {
    FooterGuide
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">
.app {
  width: 100%;
  height: 100%;
  background: #f5f5f5;
}
</style>
