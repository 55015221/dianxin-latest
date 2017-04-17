<template>
    <div class="template-wrapper">

        <Jumbotron/>

        <!--content-->
        <section class="content">
            <div class="container">
                <div class="page-title">
                        <span style="color: #3099E3;">典信</span>简介
                </div>
                <div v-for="(item, index) in records.content">
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
                        <img class="img-responsive" src="/static/images/关于我们_03.png"/>
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
    name: 'about',
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
.page-title {
    margin-top: 30px;
    font-size: 32px;
    font-weight: 500;
    text-align: center;
}
.content h2 {
    font-size:20px;
    font-weight: bold;
    margin-bottom: 15px;
}


</style>
