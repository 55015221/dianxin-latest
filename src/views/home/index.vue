<template>
    <div class="template-wrapper">
        <Carousel/>
        <!-- <Carousel/> -->

        <!--content-->
        <section class="content">
            <div class="container">
                <div class="row row-items" v-for="(item ,index) in records">
                    <div :class="(index%2 === 1)?'col-sm-7 wow slideInLeft':'col-sm-7 col-sm-push-5 wow slideInRight'">
                        <h3>{{ item.title }}</h3>
                        <div class="details">
                            <span class="lead">{{ item.lead }}</span>
                            <p class="text-muted">{{ item.content }}</p>
                        </div>
                    </div>
                    <div :class="(index%2 === 1)?'col-sm-5 wow slideInRight':'col-sm-5 col-sm-pull-7 wow slideInLeft'">
                        <img class="img-responsive center-block" data-src="/static/images/placeholder_400x250.svg" alt="400x250" :src="item.imageUrl" data-holder-rendered="true">
                    </div>
                </div>
            </div>
        </section>

        <!--PRODUCT AND SERVICE-->
        <section class="products">
            <div class="container">
                <fieldset class="wow fadeInUp">
                    <legend>
                        <h2>产品与服务</h2>
                        <span class="lead">PRODUCT AND SERVICE</span>
                    </legend>
                </fieldset>
                <div class="row wow fadeInUp">
                    <div class="col-sm-2 col-sm-offset-1">
                        <img src="/static/images/首页_13_01.png" alt="Responsive across devices" class="">
                        <h4>在线往来平台</h4>
                        <p>你的网站和应用能在 Bootstrap 的帮助下通过同一份代码快速、有效适</p>
                    </div>
                    <div class="col-sm-2">
                        <img src="/static/images/首页_13_03.png" alt="Responsive across devices" class="">
                        <h4>业务登记与交换服务</h4>
                        <p>你的网站和应用能在 Bootstrap 的帮助下通过同一份代码快速、有效适</p>
                    </div>
                    <div class="col-sm-2">
                        <img src="/static/images/首页_13_05.png" alt="Responsive across devices" class="">
                        <h4>用户认证服务</h4>
                        <p>你的网站和应用能在 Bootstrap 的帮助下通过同一份代码快速、有效适</p>
                    </div>
                    <div class="col-sm-2">
                        <img src="/static/images/首页_13_07.png" alt="Responsive across devices" class="">
                        <h4>往来账款管理咨询</h4>
                        <p>你的网站和应用能在 Bootstrap 的帮助下通过同一份代码快速、有效适</p>
                    </div>
                    <div class="col-sm-2">
                        <img src="/static/images/首页_13_09.png" alt="Responsive across devices" class="">
                        <h4>信用管理咨询</h4>
                        <p>你的网站和应用能在 Bootstrap 的帮助下通过同一份代码快速、有效适</p>
                    </div>

                </div>
            </div>
        </section>

        <!--SOULUTION-->
        <section class="soulution">
            <div class="container">
                <fieldset class="wow fadeInUp">
                    <legend>
                        <h2>解决方案</h2>
                        <span class="lead">SOULUTION</span>
                    </legend>
                </fieldset>
                <div class="row wow fadeInUp">
                    <div class="col-sm-6">
                        供应链循环业务一体化
                    </div>
                    <div class="col-sm-6">
                        销售业务一体化
                    </div>
                    <div class="col-sm-6">
                        费用报销与额度控制
                    </div>
                    <div class="col-sm-6">
                        工资核算与发放
                    </div>
                </div>
            </div>
        </section>

        <!--DEPLOYMENT WAY-->
        <section class="deploymentway">
            <div class="container">
                <fieldset class="wow fadeInUp">
                    <legend>
                        <h2>部署方式</h2>
                        <span class="lead">DEPLOYMENT WAY</span>
                    </legend>
                </fieldset>
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

    </div>
</template>


<script>
import { mapState } from 'vuex'
import Carousel from '../../components/Carousel.vue'
export default {
    name: 'index',
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
        console.log("created index")
        this.$store.dispatch('getHome',{ "method": "getHome" }).then((res) => {

        })
    },
    mounted () {
        console.log("mounted index")
    },
    methods:{

    }
}
</script>

<style scoped>
.carousel, .listbox {
    max-height: 450px;
    overflow: hidden;
}

.content {

}
h4 {
    font-size: 14px;
    margin-top: 10px;
    font-weight: bold
}

.row-items {
    padding-top: 30px;
    padding-bottom: 30px;
}

.row-items:after {
        top: 30px;
        position: relative;
        width: 100%;
        height: 1px;
        display: block;
        content: " ";
        background: linear-gradient(90deg,hsla(0,0%,56%,0),#8e8e8e,hsla(0,0%,56%,0));
}
.products, .soulution, .deploymentway {
    padding-top: 60px;
    padding-bottom: 60px;
}
.row-items:last-child:after {
    height: 0;
}

.row-items h3 {
    color:#3099E3;
    margin-top: 20px;
}
.details {
    margin-left:20px;
}
fieldset {
    width: 50%;
    margin: 0 auto;
    border-top: 1px solid #c0c0c0;
    text-align:center;
    font-weight: bold;
    line-height: 0;
}
legend {
    width:auto;
    padding: 0 20px;
}

fieldset h2 {
    color: #666;
    font-weight: 500;
    margin-bottom:0;
}
fieldset .lead {
    color:#3099E3;
    font-size: 15px;
    font-weight: 500;
}
.products .col-sm-2 {
    text-align: center;
    font-size: 13px;
}


.soulution .col-sm-6 {
    height: 200px;
    line-height: 200px;
    text-align: center;
    font-size: 20px;
    color: #fff;
}

.soulution .col-sm-6:nth-child(4n+1){background-color:#3099E3;border:10px solid #fff;}
.soulution .col-sm-6:nth-child(4n+2){background-color:#F3821F;border:10px solid #fff;}
.soulution .col-sm-6:nth-child(4n+3){background-color:#FC5C5C;border:10px solid #fff;}
.soulution .col-sm-6:nth-child(4n+4){background-color:#A8D64E;border:10px solid #fff;}


.soulution .col-sm-6:nth-child(4n+1):after {
    content: "";
    border-top-left-radius: 40px;
    border: 20px solid #fff;
    position: absolute;
    bottom: -5px;
    right: -5px;
}
.soulution .col-sm-6:nth-child(4n+2):after {
    content: "";
    border-top-right-radius: 40px;
    border: 20px solid #fff;
    position: absolute;
    bottom: -5px;
    left: -5px;
}
.soulution .col-sm-6:nth-child(4n+3):after {
    content: "";
    border-bottom-left-radius: 40px;
    border: 20px solid #fff;
    position: absolute;
    top: -5px;
    right: -5px;
}
.soulution .col-sm-6:nth-child(4n+4):after {
    content: "";
    border-bottom-right-radius: 40px;
    border: 20px solid #fff;
    position: absolute;
    top: -5px;
    left: -5px;
}

.deploymentway .col-sm-4 {
    text-align: center;
}

</style>
