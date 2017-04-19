<template>
    <div class="template-wrapper">

        <Jumbotron/>

        <!--content-->
        <section class="content">
            <div class="row items" v-for="(item ,index) in records" :style="(index%2 === 1)?'background: #e6e6e6;':''">
                <div class="container">
                    <div :class="(index%2 !== 1)?'col-sm-7 wow slideInLeft':'col-sm-7 col-sm-push-5 wow slideInRight'">
                        <div class="panel">
                            <div class="panel-heading">
                                <h3 class="panel-title">{{ item.title }}</h3>
                                <small>{{ item.lead }}</small>
                            </div>
                            <div class="panel-body">
                                {{ item.content }}
                            </div>
                        </div>
                    </div>
                    <div :class="(index%2 !== 1)?'col-sm-5 wow slideInRight':'col-sm-5 col-sm-pull-7 wow slideInLeft'">
                        <img class="img-responsive" data-src="/static/images/placeholder_400x250.svg" alt="400x250" :src="item.imageUrl" data-holder-rendered="true">
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
    name: 'product',
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
        console.log("created product")
        this.$store.dispatch('getProduct',{ "method": "getProduct" }).then((res) => {
            console.log(res)
        })
    },
    mounted () {
        console.log("mounted product")
    },
    methods:{

    }
}
</script>

<style scoped>
.content .items {
    padding: 80px 0;
}
.panel {
    background-color: inherit;
    border: none;border-radius: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
}
.panel-heading .panel-title {
    font-size: 20px;
    font-weight: 600;
}
.panel-heading small {
    color: #3099E3;
    font-size: 16px;
}
.panel-body {
    padding: 0 15px;
}
</style>
