<template>
    <div class="template-wrapper">

        <Jumbotron/>

        <!--content-->
        <section class="content">
            <div class="container">
                <div class="page-title">
                    <span style="color: #3099E3;">典信</span>简介
                </div>
                <article v-for="(item, index) in records.content">
                    <h2>公司成立</h2>
                    <p>{{ item }}</p>
                </article>
            </div>
        </section>
        <section class="content">
            <div class="container">
                <div class="page-title">
                        <span style="color: #3099E3;">典信</span>荣誉
                </div>
                <article class="row">
                    <div class="col-sm-6" style="margin-top:30px;">
                        <h2>Successful <span style="color: #3099E3;">cases</span><br/>企业荣誉</h2>
                        <p v-for="(item, index) in records.content">
                            {{ item }}
                        </p>
                    </div>
                    <div class="col-sm-6">
                        <img class="img-responsive" src="/static/images/关于我们_03.png"/>
                    </div>
                </article>
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
    padding: 20px 0;
    font-size: 26px;
    font-weight: 700;
    text-align: center;
}
article {
    margin-bottom: 10px;
}
.content h2 {
    font-size: 18px;
    font-weight: 600;
}


</style>
