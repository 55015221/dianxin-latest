<template>
    <footer class="footer">
        <div class="container">
            <div class="row hidden-xs">
                <dl class="col-sm-2 site-link">
                    <dt>关于</dt>
                    <dd><a href="/about">关于我们</a></dd>
                    <dd><a href="/contact">联系我们</a></dd>
                </dl>
                <dl class="col-sm-2 site-link">
                    <dt>产品与服务</dt>
                    <dd><a href="/product">软件产品</a></dd>
                    <dd><a href="/product">云平台服务</a></dd>
                    <dd><a href="/product">基础服务</a></dd>
                    <dd><a href="/product">增值服务</a></dd>
                    <dd><a href="/product">咨询服务</a></dd>
                </dl>
                <dl class="col-sm-2 site-link">
                    <dt>业务合作</dt>
                    <dd><a href="/solution">市场推广合作</a></dd>
                    <dd><a href="/solution">供应链金融合作</a></dd>
                </dl>
                <dl class="col-sm-2 site-link">
                    <dt>解决方案</dt>
                    <dd><a href="/solution">供应链与应付</a></dd>
                    <dd><a href="/solution">销售、分销与应收</a></dd>
                    <dd><a href="/solution">报销业务</a></dd>
                    <dd><a href="/solution">工资业务</a></dd>
                </dl>
                <dl class="col-sm-3 col-sm-offset-1 site-link" id="license">
                    <dd><span class="glyphicon glyphicon-phone-alt"></span> 4007751007</dd>
                    <dd><span class="glyphicon glyphicon-map-marker"></span> 深圳市龙岗区大运软件小镇54栋306</dd>
                    <dd><img width="100" height="100" src="/static/images/qrcode.png"/></dd>
                </dl>
            </div>
        </div>
        <div class="copyright">
            <div class="container">
                Copyright © 2011-2017 典信科技有限公司. All Rights Reserved &nbsp;<br />
                <a href="http://www.miibeian.gov.cn/" rel="nofollow">粤ICP备 15005796号-3</a> &nbsp;
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
    margin-bottom: 10px;
    color: #333;
}
.footer .site-link dd {
    margin: 5px 0;
    font-size: 13px;
}
.copyright {
    background: #444;
    color: #ccc;
    text-align: right;
}

</style>
