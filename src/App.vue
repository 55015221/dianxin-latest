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
                        <a href="/" class="navbar-brand"><img class="img-responsive" height="50" src="/static/images/logo.jpg"/></a>
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
            <div class="container">
                <div class="row">
                    <div class="col-sm-8 col-xs-12">
                          <div class="col-xs-3">
                            <h4>关于</h4>
                            <ul class="list-unstyled">
                              <li><a href="/about">关于我们</a></li>
                              <li><a href="/contact">联系我们</a></li>
                            </ul>
                          </div>
                          <div class="col-xs-3">
                            <h4>产品与服务</h4>
                            <ul class="list-unstyled">
                              <li><a href="/product">软件产品</a></li>
                              <li><a href="/product">云平台服务</a></li>
                              <li><a href="/product">基础服务</a></li>
                              <li><a href="/product">增值服务</a></li>
                              <li><a href="/product">咨询服务</a></li>
                            </ul>
                          </div>
                          <div class="col-xs-3">
                            <h4>业务合作</h4>
                            <ul class="list-unstyled">
                              <li><a href="/solution">市场推广合作</a></li>
                              <li><a href="/solution">供应链金融合作</a></li>
                            </ul>
                          </div>
                          <div class="col-xs-3">
                            <h4>解决方案</h4>
                            <ul class="list-unstyled">
                              <li><a href="/solution">供应链与应付</a></li>
                              <li><a href="/solution">销售、分销与应收</a></li>
                              <li><a href="/solution">报销业务</a></li>
                              <li><a href="/solution">工资业务</a></li>
                            </ul>
                          </div>

                    </div>
                    <div class="col-sm-3 col-sm-offset-1 col-xs-12">
                        <div class="qr">
                            <p><span class="glyphicon glyphicon-phone-alt"></span> 4007751007</p>
                            <p><span class="glyphicon glyphicon-map-marker"></span> 深圳市龙岗区大运软件小镇54栋306</p>
                            <p><img width="100" height="100" src="/static/images/qrcode.png"/></p>
                        </div>
                    </div>
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
.navbar-brand {
    padding: 0 15px;
}
.navbar-brand img {
    height: 50px;
}
.footer  {
    text-align: left;
}
.footer .row {
    padding-top: 30px;
    padding-bottom: 30px;
}
.footer h4 {
    font-size: 15px;
    font-weight:600;
}
.footer .col-sm-8 {
    border-right: 1px solid #ddd;
}
.footer .col-sm-4 {
    border-left: 1px solid #fff;
}

</style>
