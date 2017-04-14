<template>

    <div id="app">

        <!--header 头部-->
        <!--<header class="header navbar-fixed-top">-->
        <header class="header">
            <div class="container">
                <div class="navbar navbar-default">
                    <div class="navbar-header">
                        <button class="navbar-toggle" type="button" data-toggle="collapse" data-target="#bs-navbar"
                                aria-controls="bs-navbar" aria-expanded="true">
                            <span class="sr-only">Toggle navigation</span>
                            <span class="icon-bar"></span>
                            <span class="icon-bar"></span>
                            <span class="icon-bar"></span>
                        </button>
                        <a href="/" class="navbar-brand">Logo</a>
                    </div>
                    <nav id="bs-navbar" class="navbar-collapse collapse" aria-expanded="true">
                        <ul class="nav navbar-nav navbar-right">
                            <template v-for="(item, index) in menuList">
                                <router-link :to="item.link" tag="li"><a href="">{{ item.label }}</a></router-link>
                            </template>
                        </ul>
                        <!--
                        <ul class="nav navbar-nav navbar-right">
                            <li><a href="">管理后台</a></li>
                        </ul>
                        -->
                    </nav>
                </div>
            </div>
        </header>

        <!--wrapper 主体-->
        <main class="wrapper">
            <transition name="router-fade" mode="out-in">
              <router-view></router-view>
            </transition>
        </main>

        <!--header 底部-->
        <footer class="footer">
            <div class="row">
                <div class="col-sm-8 col-sm-offset-1">
                      <div class="col-xs-3">
                        <h4>关于</h4>
                        <ul class="list-unstyled">
                          <li><a href="/about/">关于我们</a></li>
                          <li><a href="/ad/">广告合作</a></li>
                          <li><a href="/links/">友情链接</a></li>
                          <li><a href="/hr/">招聘</a></li>
                        </ul>
                      </div>
                      <div class="col-xs-3">
                        <h4>联系方式</h4>
                        <ul class="list-unstyled">
                          <li><a href="http://weibo.com/bootcss" title="Bootstrap中文网官方微博" target="_blank">新浪微博</a></li>
                          <li><a href="mailto:admin@bootcss.com">电子邮件</a></li>
                        </ul>
                      </div>
                      <div class="col-xs-3">
                        <h4>旗下网站</h4>
                        <ul class="list-unstyled">
                          <li><a href="http://www.golaravel.com/" target="_blank">Laravel中文网</a></li>
                          <li><a href="http://www.ghostchina.com/" target="_blank">Ghost中国</a></li>
                        </ul>
                      </div>
                      <div class="col-xs-3">
                        <h4>赞助商</h4>
                        <ul class="list-unstyled">
                          <li><a href="http://www.ucloud.cn/" target="_blank">UCloud</a></li>
                          <li><a href="https://www.upyun.com" target="_blank">又拍云</a></li>
                        </ul>
                      </div>

                </div>
                <div class="col-sm-3">
                    <p>123456789</p>
                    <p>本网站所列开源项目的中文版文档全部</p>
                    <p><img width="100" height="100" src="/static/images/placeholder_400x250.svg"/></p>
                </div>
            </div>
            <div class="bottom">
                <div class="container">
                    <div style="transform: translate(0px, 0px); opacity: 1;">
                        <span>Copyright &copy; 2017 The Project by <a href="#">Basicredit.com</a>. All Rights Reserved</span>
                   </div>
                </div>
            </div>
        </footer>

    </div>

</template>

<script>
import { mapState } from 'vuex'

export default {
  name: 'app',
  data () {
    return {

    }
  },
  components: {

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
.footer .col-xs-3 {
    text-align: left;
}
.footer h4 {
    font-size:13px;
    font-weight:bold;
}
.footer .col-sm-9 {
    border-right: 1px solid #ddd;
}
.footer .col-sm-3 {
    border-left: 1px solid #fff;
}

</style>
