<template>
    <div class="template-wrapper">
        <!-- <Carousel/> -->
        <Carousel/>

        <!--content-->
        <div class="wrapper-content">
            <!--INTRODUCE-->
            <section class="introduce">
                <div class="container">
                    <template v-for="(item ,index) in records.product">
                        <div class="row items">
                            <div :class="(index%2 === 1)?'col-sm-7 wow slideInLeft':'col-sm-7 col-sm-push-5 wow slideInRight'">
                                <div class="panel">
                                    <div class="panel-heading">
                                        <h3 class="panel-title">{{ item.title }}</h3>
                                        <small>{{ item.lead }}</small>
                                    </div>
                                    <div class="panel-body">
                                        <p>{{ item.content }}</p>
                                    </div>
                                </div>
                            </div>
                            <div :class="(index%2 === 1)?'col-sm-5 wow slideInRight':'col-sm-5 col-sm-pull-7 wow slideInLeft'">
                                <img class="img-responsive center-block"
                                     data-src="/static/images/placeholder_400x250.svg" alt=""
                                     :src="item.imageUrl" data-holder-rendered="true">
                            </div>
                        </div>
                        <div v-if="index < (records.length -1)" class="cut-off-divider"></div>
                    </template>
                </div>
            </section>

            <!--PRODUCT AND SERVICE-->
            <section class="product">
                <div class="container">
                    <div class="row-title wow fadeInUp">
                        <h2>产品与服务<span>PRODUCT AND SERVICE</span></h2>
                    </div>
                    <div class="row wow fadeInUp">
                        <template v-for="(item ,index) in records.service">
                            <router-link to="/product" :class="(index == 0) ? 'col-sm-2 col-sm-offset-1': 'col-sm-2'"
                            v-on:mouseenter="onEnter(item.hoverUrl)"
                            v-on:mouseleave="onLeave(item.imageUrl)">
                                <img :src="item.imageUrl" :data-hover="item.hoverUrl" alt="" class="">
                                <h4>{{ item.title }}</h4>
                                <p>{{ item.content }}</p>
                            </router-link>
                        </template>
                    </div>
                </div>
            </section>

            <!--SOLUTION-->
            <section class="solution">
                <div class="container">
                    <div class="row-title wow fadeInUp">
                        <h2>解决方案<span>SOULUTION</span></h2>
                    </div>
                    <div class="row wow fadeInUp">
                        <a href="/solution" v-link="{path: '/solution'}" class="col-sm-6">
                            <span class="glyphicon glyphicon-link"></span>
                            供应链业务一体化
                        </a>
                        <a href="/solution" v-link="{path: '/solution'}" class="col-sm-6">
                            <span class="glyphicon glyphicon-paperclip"></span>
                            销售业务一体化
                        </a>
                        <a href="/solution" v-link="{path: '/solution'}" class="col-sm-6">
                            <span class="glyphicon glyphicon-erase"></span>
                            费用报销与额度控制
                        </a>
                        <a href="/solution" v-link="{path: '/solution'}" class="col-sm-6">
                            <span class="glyphicon glyphicon-transfer"></span>
                            业务机器人
                        </a>
                    </div>
                </div>
            </section>

            <!--DEPLOYMENT-->
            <section class="deployment">
                <div class="container">
                    <div class="row-title wow fadeInUp">
                            <h2>部署方式<span>DEPLOYMENT WAY</span></h2>
                    </div>
                    <div class="row wow fadeInUp">
                        <div class="col-sm-4">
                            <img src="/static/images/首页_17.png" alt="Responsive across devices" class="">
                            <h4>企业内部部署</h4>
                        </div>
                        <div class="col-sm-4">
                            <img src="/static/images/首页_19.png" alt="Responsive across devices" class="">
                            <h4>服务器托管</h4>
                        </div>
                        <div class="col-sm-4">
                            <img src="/static/images/首页_21.png" alt="Responsive across devices" class="">
                            <h4>SAAS云模式</h4>
                        </div>
                    </div>
                </div>
            </section>

            <!--CUSTOMER-->
            <section class="customer">
                <div class="container">
                    <div class="row wow fadeInUp">
                        <div class="col-sm-6">
                            <img src="/static/images/customer/01.png" alt="">
                        </div>
                        <div class="col-sm-6">
                            <div class="row-title wow fadeInUp">
                                    <h2>主要客户<span>CLIENT</span></h2>
                            </div>
                            <div class="row">
                                <div class="col-sm-3 col-sm-offset-1"><img src="/static/images/customer/changfeng.jpg" alt="" class="img-responsive"></div>
                                <div class="col-sm-3 col-sm-offset-1"><img src="/static/images/customer/lingchuang.png" alt="" class="img-responsive"></div>
                                <div class="col-sm-3 col-sm-offset-1"><img src="/static/images/customer/lizhi.jpg" alt="" class="img-responsive"></div>
                                <div class="col-sm-3 col-sm-offset-1"><img src="/static/images/customer/shicheng.png" alt="" class="img-responsive"></div>
                                <div class="col-sm-3 col-sm-offset-1"><img src="/static/images/customer/dagong.png" alt="" class="img-responsive"></div>
                                <div class="col-sm-3 col-sm-offset-1"><img src="/static/images/customer/keguang.png" alt="" class="img-responsive"></div>
                                <div class="col-sm-3 col-sm-offset-1"><img src="/static/images/customer/gp.png" alt="" class="img-responsive"></div>
                                <div class="col-sm-3 col-sm-offset-1"><img src="/static/images/customer/kelu.png" alt="" class="img-responsive"></div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

        </div>
    </div>
</template>

<script>
import { mapState } from 'vuex'
import Carousel from '../../components/Carousel.vue'
export default {
    name: 'home',
    data () {
        return {
            colors: [
                "#fff", "#d2eafb", "#fde3cf", "#cfedf0", "#f7f7f7"
            ]
        }
    },
    components: {
        Carousel: Carousel
    },
    computed: {
        ...mapState({
            records: state => state.module.records
        })
    },
    created () {
        console.log("created home")
        this.$store.dispatch('getHome',{ "method": "getHome" }).then((res) => {

        })
    },
    mounted () {
        console.log("mounted home")
    },
    methods:{
        onEnter: function(url){
            let img = event.target.getElementsByTagName("img");
            img[0].setAttribute('src',url)
            img[0].style.transform = "rotate3d(0,1,0,360deg)"
        },
        onLeave: function(url){
            let img = event.target.getElementsByTagName("img");
            img[0].setAttribute('src',url)
            img[0].style.transform = "rotate3d(0,1,0,0deg)"
        }
    }
}
</script>

<style scoped>
.wrapper-content {

}
.items {
    padding: 20px 0;
}

.items .panel {
    margin-top: 40px;
}

section {
    padding-top: 60px;
    padding-bottom: 60px;
}

.panel {
    background-color: inherit;
    border: none;border-radius: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
}
.panel-heading .panel-title {
    font-size: 26px;
    margin-bottom: 5px;
}
.panel-heading small {
    color: #3099E3;
    font-size: 20px;
}
.panel-body {
    padding: 0 15px;
}

fieldset {
    border-top: 1px solid #c0c0c0;
    text-align:center;
    font-weight: bold;
    line-height: 0;
}
legend {
    width:auto;
    padding: 0 20px;
    border: none;
}

fieldset h2 {
    color: #666;
    font-weight: 500;
    margin-bottom:0;
}
fieldset .lead {
    color:#3099E3;
    font-weight: 500;
}
.product .col-sm-2 {
    text-align: center;
    cursor: pointer;
}
.product h4,
.deployment h4 {
    margin-top: 30px;
    font-size: 18px;
    font-weight: 500;
}

.solution .col-sm-6 {
    height: 200px;
    line-height: 200px;
    text-align: center;
    font-size: 26px;
    color: #f8f8f8;
}

.solution .col-sm-6:nth-child(4n+1){background-color:#3099E3;border:10px solid #fff;}
.solution .col-sm-6:nth-child(4n+2){background-color:#F3821F;border:10px solid #fff;}
.solution .col-sm-6:nth-child(4n+3){background-color:#FC5C5C;border:10px solid #fff;}
.solution .col-sm-6:nth-child(4n+4){background-color:#A8D64E;border:10px solid #fff;}


.solution .col-sm-6:nth-child(4n+1):after {
    content: "";
    border-top-left-radius: 40px;
    border: 20px solid #fff;
    position: absolute;
    bottom: -5px;
    right: -5px;
}
.solution .col-sm-6:nth-child(4n+2):after {
    content: "";
    border-top-right-radius: 40px;
    border: 20px solid #fff;
    position: absolute;
    bottom: -5px;
    left: -5px;
}
.solution .col-sm-6:nth-child(4n+3):after {
    content: "";
    border-bottom-left-radius: 40px;
    border: 20px solid #fff;
    position: absolute;
    top: -5px;
    right: -5px;
}
.solution .col-sm-6:nth-child(4n+4):after {
    content: "";
    border-bottom-right-radius: 40px;
    border: 20px solid #fff;
    position: absolute;
    top: -5px;
    left: -5px;
}

.deployment .col-sm-4 {
    text-align: center;
}
.customer .col-sm-3 {
    height: 60px;
    text-align: center;
    border: 1px solid #ccc;
    margin-top: 5px;
    margin-bottom: 5px;
    overflow: hidden;
}
.introduce .panel-body p{
    text-indent:30px;  
}


</style>
