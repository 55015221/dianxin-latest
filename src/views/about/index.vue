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
            <div class="container">
                <div class="page-title">
                        <span style="color: #3099E3;">典信</span>简介
                </div>
                <div v-for="(item, index) in records.content"  style="margin-top: 30px;">
                    <h2>公司成立</h2>
                    <p>{{ item }}</p>
                </div>
            </div>
        </section>
        <section class="content">
            <div class="container">
                <div class="page-title">
                        <span style="color: #3099E3;">典信</span>荣誉
                </div>
                <div class="row">
                    <div class="col-sm-6" style="margin-top:30px;">
                        <h2>Successful <span style="color: #3099E3;">cases</span><br/>企业荣誉</h2>
                        <p v-for="(item, index) in records.content">
                            {{ item }}
                        </p>
                    </div>
                    <div class="col-sm-6">
                        <img src="/static/images/关于我们_03.png"/>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>


<script>

import { mapState } from 'vuex'

export default {
    name: 'about',
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
        console.log("created about")
        this.$store.dispatch('getAbout',{ "method": "getAbout" }).then((res) => {
            console.log(res)
        })
    },
    mounted () {
        console.log("mounted about")
    },
    methods:{

    }
}
</script>

<style scoped>
section {margin-top:80px;}
.page-title {
    font-size: 32px;
    font-weight: 500;
    text-align: center;
    margin: 20px auto;
}
.content h2 {
    font-size:20px;
    font-weight: bold;
    margin-bottom: 15px;
}


</style>
