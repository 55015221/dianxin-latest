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
                   <h2>What is your problem?</h2>
                   <ul class="list-unstyled">
                        <li v-for="(item, index) in records">
                            <div class="title">{{ item.title }}</div>
                            <div class="body">{{ item.content }}</div>
                        </li>
                   </ul>
            </div>
        </section>
    </div>
</template>


<script>

import { mapState } from 'vuex'

export default {
    name: 'questions',
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
        console.log("created questions")
        this.$store.dispatch('getQuestions',{ "method": "getQuestions" }).then((res) => {
            console.log(res)
        })
    },
    mounted () {
        console.log("mounted questions")
    },
    methods:{

    }
}
</script>

<style scoped>

.content h2 {
    margin-top: 60px;
    margin-bottom: 30px;
    color: #3099E3;
    text-align: center;
}
.content li {
    margin: 10px 0;
}
.content li .title {
    font-size: 15px;
    font-weight: 700;
    margin-bottom: 5px;
}
</style>
