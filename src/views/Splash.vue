<template>

  <div class="splashscreen-wrapper">
    <transition @leave="leaveEl" v-on:after-appear="leaveEl"  appear>
      <div class="logo-wrapper">
      </div>
     </transition>
    <div class="logo-letters-group">
      <span class="logo-letter" v-for="(item, index) in logoName" :key="index" >{{item}}</span>
    </div>
  </div>


</template>
<script>
export default {
  name: 'SplashScreen',
  data () {
    return {
      show: true,
      logoName: ['ORGANIZATION', '  ', 'STARTS', '  ', 'HERE', '  ',]
    }
  },
  methods: {
    leaveEl (el) {
      this.$router.push('/home')
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../style/splashScreen.scss'
</style>