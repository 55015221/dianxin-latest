<template>
    <div class="template-wrapper">

        <Jumbotron/>

        <!--content-->
        <section class="introduce">
            <div class="container">
                <h2><span>典信</span>简介</h2>
                <div class="panel" v-for="(item, index) in records.introduce">
                    <div class="panel-heading">
                        <h3 class="panel-title"><small style="color:#444;">{{ item.title }}</small></h3>
                    </div>
                    <div class="panel-body">
                        <p>{{ item.content }}</p>
                    </div>
                </div>
            </div>
        </section>

        <section class="honor">
            <div class="container">
                <h2><span>理论发展</span>知识产权</h2>
                <div class="row">
            
                    <div class="col-sm-6">
                        <img class="img-responsive" v-bind:src="records.honours.imageUrl"/>
                    </div>

                     <div class="col-sm-6">
                        <img class="img-responsive" src="/static/images/about1.png"/>
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

section {
    margin: 60px 0;
}

.honor h2,
.introduce h2 {
    margin-bottom: 15px;
    text-align: center;
    font-size: 38px;
}
.honor h2 span,
.honor .panel-title span,
.introduce h2 span {
    color: #3099E3;
}
.panel {
    background-color: inherit;
    border: none;border-radius: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
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
.panel-body {
    padding: 0 15px;
}
.panel-body p{
    text-indent:30px;  
}

</style>
