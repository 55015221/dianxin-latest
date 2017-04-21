<template>

    <div id="app">
        <!--header 头部-->
        <Header v-bind:menuList="menuList"/>

        <!--wrapper 主体-->
        <main class="wrapper">
            <transition name="router-fade" mode="out-in">
              <router-view></router-view>
            </transition>
        </main>

        <!--footer 底部-->
        <Footer />
    </div>

</template>

<script>
import { mapState } from 'vuex'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'app',
  data () {
    return {

    }
  },
  components: {
    Header: Header,
    Footer: Footer
  },
  computed: {
      ...mapState({
          menuList: state => state.module.menuList
      })
  },
  created () {
      console.log("created app")
      this.$store.dispatch('getMenuList',{"method":"getMenuList"}).then((res) =>{

      })
  },
  mounted () {
      console.log("mounted app")
      //初始化动画
      new WOW().init();
  }
}
</script>

<style scoped>
#app {}

.router-fade-enter-active, .router-fade-leave-active {
      transition: opacity .3s;
}
.router-fade-enter, .router-fade-leave-active {
      opacity: 0;
}
</style>
