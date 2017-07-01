<template>
    <footer class="footer">
        <div class="container hidden-xs">
            <div class="row">
                <dl class="col-sm-2 site-link">
                    <dt>关于</dt>
                    <dd><router-link to="/about">关于我们</router-link></dd>
                    <dd><router-link to="/contact">联系我们</router-link></dd>
                </dl>
                <dl class="col-sm-2 site-link">
                    <dt>产品与服务</dt>
                    <dd><router-link to="/product">软件产品</router-link></dd>
                    <dd><router-link to="/product">云平台服务</router-link></dd>
                    <dd><router-link to="/product">数据交换服务</router-link></dd>
                    <dd><router-link to="/product">增值服务</router-link></dd>
                    <dd><router-link to="/product">实施、咨询服务</router-link></dd>
                </dl>
                <dl class="col-sm-2 site-link">
                    <dt>解决方案</dt>
                    <dd><router-link to="/solution">供应链与应付</router-link></dd>
                    <dd><router-link to="/solution">销售、分销与应收</router-link></dd>
                    <dd><router-link to="/solution">报销业务</router-link></dd>
                    <dd><router-link to="/solution">工资业务</router-link></dd>
                    <dd><router-link to="/solution">业务机器人</router-link></dd>
                </dl>
                <dl class="col-sm-3 col-sm-offset-1 site-link" id="license">
                    <dd><span class="glyphicon glyphicon-phone-alt"></span> 0755-29964020</dd>
                    <dd><span class="glyphicon glyphicon-map-marker"></span> 深圳市龙岗区大运软件小镇27栋207</dd>
                    <!--<dd><img width="100" height="100" src="/static/images/qrcode.png"/></dd>-->
                </dl>
            </div>
        </div>
        <div class="copyright">
            <div class="container">
                Copyright © 2017 典信科技有限公司. All Rights Reserved &nbsp;<br />
                <a href="http://www.miibeian.gov.cn/" rel="nofollow">粤ICP备11086626号</a> &nbsp;
            </div>
        </div>
    </footer>
</template>


<script>

export default {
    name: 'footer',
    data () {
        return {
        }
    },
    components: {
    },
    computed: {
    },
    created () {
        console.log("created footer")
    },
    mounted () {
        console.log("mounted footer")
    },
    methods:{

    }
}
</script>

<style>

.footer {
    font-size: 14px;
    background: #e9e9e9;
}
.footer .container {
    padding: 30px 0;
}
.copyright .container {
    padding: 15px 0;
}
.footer a {
    color: #666;
}
.footer .site-link dt {
    margin-bottom: 5px;
    color: #333;
}
.footer .site-link dd {
    line-height: 1.6;
    font-size: 14px;
}
.copyright {
    background: #444;
    color: #ccc;
    text-align: right;
}

</style>
