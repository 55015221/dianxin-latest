<template>
    <div class="template-wrapper">

        <div style="background: #3099E3 url('/static/images/首页_02.png');margin: 0;">
            <div class="" style="width:1500px; margin:0 auto;">
                <img class="first-slide" src="/static/images/解决方案_02.png" alt="First slide">
            </div>
            <!--
            <div class="jumbotron wow zoomIn">
                <div class="container text-center">
                    <h2>关于我们</h2>
                </div>
            </div>
            -->
        </div>

        <!--content-->
        <section class="content">
            <div class="row">
                <div class="container">
                    <div class="col-sm-6">
                         <h2>供应链循环业务一体化</h2>
                         <ul>
                             <li>实现供应链业务在线处理</li>
                             <li>实现与供应商的在线协同</li>
                             <li>全面掌控供应链实时情况</li>
                             <li>提升供应商效率，消除对账</li>
                         </ul>
                    </div>
                    <div class="col-sm-6">
                        <img class="img-responsive center-block" data-src="/static/images/placeholder_400x250.svg" alt="400x250" src="/static/images/解决方案_03.png" data-holder-rendered="true">
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>


<script>

import { mapState } from 'vuex'

export default {
    name: 'solution',
    data () {
        return {
        }
    },
    components: {
    },
    computed: {
        ...mapState({
            records: state => state.module.records
        })
    },
    created () {
        console.log("created solution")
        this.$store.dispatch('getProduct',{ "method": "getProduct" }).then((res) => {
            console.log(res)
        })
    },
    mounted () {
        console.log("mounted solution")
    },
    methods:{

    }
}
</script>

<style scoped>
.content .row {
    padding: 80px 0;
}
.content h2 {
    margin-top: 100px;
    color: #3099E3;
}
.content ul {
    margin-left: 18px;
}
</style>
