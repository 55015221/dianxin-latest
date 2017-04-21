<template>
    <div class="template-wrapper">

        <Jumbotron/>

        <!--content-->
        <section class="content">
            <div class="container">
                <div class="row">
                    <ul class="nav nav-tabs" role="tablist">
                        <li role="presentation" class="active"><a href="#panel-1" role="tab" data-toggle="tab"
                                                                  aria-controls="profile" aria-expanded="true">供应链业务</a></li>
                        <li role="presentation" class=""><a href="#panel-2" role="tab" data-toggle="tab" aria-controls="profile"
                                                            aria-expanded="false">销售业务</a></li>
                        <li role="presentation" class=""><a href="#panel-3" role="tab" data-toggle="tab" aria-controls="profile"
                                                            aria-expanded="false">费用报销</a></li>
                        <li role="presentation" class=""><a href="#panel-4" role="tab" data-toggle="tab" aria-controls="profile"
                                                            aria-expanded="false">工资核算</a></li>
                    </ul>
                    <div class="tab-content">
                        <div role="tabpanel" class="tab-pane fade active in" id="panel-1" aria-labelledby="profile-tab">
                            <div class="col-sm-4">
                                <div class="panel">
                                    <div class="panel-heading">
                                        <h3 class="panel-title">供应链循环业务一体化</h3>
                                        <small></small>
                                    </div>
                                    <div class="panel-body">
                                        <ul>
                                            <li>实现供应链业务在线处理</li>
                                            <li>实现与供应商的在线协同</li>
                                            <li>全面掌控供应链实时情况</li>
                                            <li>提升供应商效率，消除对账</li>
                                        </ul>
                                    </div>
                                </div>
                            </div>
                            <div class="col-sm-8">
                                <img class="img-responsive center-block" data-src="/static/images/placeholder_400x250.svg"
                                     alt="" src="/static/images/solution/01.png" data-holder-rendered="true">
                            </div>
                        </div>
                        <div role="tabpanel" class="tab-pane fade" id="panel-2" aria-labelledby="profile-tab">
                            <div class="col-sm-4">
                                <div class="panel">
                                    <div class="panel-heading">
                                        <h3 class="panel-title">供应链循环业务一体化</h3>
                                        <small></small>
                                    </div>
                                    <div class="panel-body">
                                        <ul>
                                            <li>实现供应链业务在线处理</li>
                                            <li>实现与供应商的在线协同</li>
                                            <li>全面掌控供应链实时情况</li>
                                            <li>提升供应商效率，消除对账</li>
                                        </ul>
                                    </div>
                                </div>
                            </div>
                            <div class="col-sm-8">
                                <img class="img-responsive center-block" data-src="/static/images/placeholder_400x250.svg"
                                     alt="" src="/static/images/solution/02.png" data-holder-rendered="true">
                            </div>
                        </div>
                        <div role="tabpanel" class="tab-pane fade" id="panel-3" aria-labelledby="profile-tab">
                            <div class="col-sm-4">
                                <div class="panel">
                                    <div class="panel-heading">
                                        <h3 class="panel-title">供应链循环业务一体化</h3>
                                        <small></small>
                                    </div>
                                    <div class="panel-body">
                                        <ul>
                                            <li>实现供应链业务在线处理</li>
                                            <li>实现与供应商的在线协同</li>
                                            <li>全面掌控供应链实时情况</li>
                                            <li>提升供应商效率，消除对账</li>
                                        </ul>
                                    </div>
                                </div>
                            </div>
                            <div class="col-sm-8">
                                <img class="img-responsive center-block" data-src="/static/images/placeholder_400x250.svg"
                                     alt="" src="/static/images/solution/03.png" data-holder-rendered="true">
                            </div>
                        </div>
                        <div role="tabpanel" class="tab-pane fade" id="panel-4" aria-labelledby="profile-tab">
                            <div class="col-sm-4">
                                <div class="panel">
                                    <div class="panel-heading">
                                        <h3 class="panel-title">供应链循环业务一体化</h3>
                                        <small></small>
                                    </div>
                                    <div class="panel-body">
                                        <ul>
                                            <li>实现供应链业务在线处理</li>
                                            <li>实现与供应商的在线协同</li>
                                            <li>全面掌控供应链实时情况</li>
                                            <li>提升供应商效率，消除对账</li>
                                        </ul>
                                    </div>
                                </div>
                            </div>
                            <div class="col-sm-8">
                                <img class="img-responsive center-block" data-src="/static/images/placeholder_400x250.svg"
                                     alt="" src="/static/images/solution/04.png" data-holder-rendered="true">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>


<script>

import { mapState } from 'vuex'
import Jumbotron from '../../components/Jumbotron.vue'

export default {
    name: 'solution',
    data () {
        return {
        }
    },
    components: {
        Jumbotron: Jumbotron
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
section {
    padding-top: 60px;
    padding-bottom: 60px;
}
.panel {
    margin-top: 40px;
}
.panel-heading .panel-title {
    font-size: 30px;
    font-weight: 600;
}
.panel-heading small {
    color: #3099E3;
    font-size: 20px;
    font-weight: 600;
}
.panel .panel-body li {
    line-height: 1.8;
}
.nav-tabs li.active a {
    color: #3099E3;
}
</style>
